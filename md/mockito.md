#Unit Testing with Mockito


-
-
### Vocabulary

- System Under Test (SUT) - The component being tested (usually an object or method)
- Indirect inputs - inputs to SUT other than argument parameters that may change behavior (eg: return values or thrown exceptions from objects/methods used by SUT)
- Context switch - directing your attention away from the current task on to a different one, often due to distraction or interruption.

-
### Unit test reminders

Unit tests should be:

- **Fast** - sub-second runtime; Developers shouldn't have time for context switching while tests run.
- **Independent** - the results or order of other tests should not matter
- **Consistent** - same result every time, everywhere
- **Short** - 
- **Isolated** - no dependencies on DB, Internet, or File System availability/state
- **No side effects** - Running tests should not impact production behavior

-
-
## Test Doubles


-
### Types of Test Doubles

- Dummy objects
- Stubs
- Spies
- Mocks
- Fakes

-
### Dummy objects

- Used as a mandatory argument to methods (often constructor/builder)
- No behavior, not directly interacted with

-
### Stubs

- Used to force specific conditions for the SUT to respond to
- Generally contains minimal logic, just enough to get the job done
- Often used in place of components which may not reliably produce the desired conditions eg: to test behavior when a SQLException occurs

-
### Spies

- Used to verify certain methods were/n't called, with certain arguments
- Usually calls the real methods, keeping track of arguments/returns for later verification
- May stub certain methods as needed

-
### Mocks

- Take the place of actual objects for the sake of testing
- Provide adequate (often stubbed) behavior for testing purposes


-
### Fakes

- Implements same functionality as the component it replaces
- Implementation is usually much simpler and/or faster, not suitable for production
- Example: fake in-memory persistence layer


-
### Mockito cannot Mock/spy:

- Final classes
- private, static, or final methods
- enums
- `hashCode()` and `equals()` methods
- Anonymous classes
- primitive types

-
### Mocking objects

```
BigComplexObject bcoMock = Mockito.mock(BigComplexObject.class);
```

- Works on interfaces or concrete classes.
- Mocked object will return default values for return types of methods
- Specify custom returns by stubbing

-
### @Mock

Alternative to calling `Mockito.mock()`, saves a few keystrokes.

```
@Mock
BigComplicatedObject bcoMock;
```


-
## Caveat Illusor

The `@Mock` Annotation must be used in combination with either:

- `@RunWith(MockitoJUnitRunner.class)` on the whole class

**OR**

- `Mockito.initMocks()` somewhere before the mock is used (eg: in the `@Before`)

-
### Stubbing

Use `when(...)` with `thenReturn(...)` and `thenThrow(...)` to stub method calls and their responses.

Specify sequential responses with `thenReturn(<first>, <second>, ..., <nth>, <all others>)`

-
### Examples

```
@Test
public void currency_exchange_coverts_currency_at_given_rate(){
	when(bcoMock.getUSDExchangeRate("GBP")).thenReturn(1.4);
	when(bcoMock.getJPYExchangeRate(anyString())).thenReturn(100);
	CurrencyExchange sut = new CurrencyExchange(bcoMock);
	assertTrue(25, sut.exchange("¥2500", "USD"));
```

**Note**: Stubbed methods that use matcher must use them for all arguments

```
verify(mock).someMethod(anyInt(), anyString(), eq("third argument"));
verify(mock).someMethod(1, anyString(), "third argument"); // Fails!!!
```

-
### Stubbing with Callbacks

When you need more granular responses to methods calls, `thenAnswer()` provides callback functionality.


```
when(mock.someMethod(anyString())).thenAnswer(new Answer() {
     Object answer(InvocationOnMock invocation) {
         Object[] args = invocation.getArguments();
         Object mock = invocation.getMock();
         return "called with arguments: " + args;
     }
 });
```

**Caution**: This may be a sign you need to refactor.

-
### Verify()

Verify that certain interactions did/n't occur on a mocked object

- `verifyZeroInteractions(Mock...)` - useful for dummy objects
- `verify(aMock, times(2)).someMethod()` - check that `aMock.someMethod` was called twice

-
### Matchers

Lots of matchers available, some examples:

`any`, `anyOf`, `allOf`, `both`, `either`, `is`, `not`, `notNullValue`, `NullValue`, `anything`, `hasItem`, `instanceOf`, `sameInstance`...


-
-
### Related topics
- Hamcrest matchers
- PowerMock

-
### Resources

- [Test Doubles](http://xunitpatterns.com/Test%20Double.html) from xUnit Patterns
- [Mockito Website](http://mockito.org/)
- [Mockito Essentials (Packt)](https://www.packtpub.com/packtlib/book/Application%20Development/9781783983605)
- [Mockito Cookbook (Packt)](https://www.packtpub.com/application-development/mockito-cookbook)
- [Martin Fowler on Test Doubles](http://martinfowler.com/bliki/TestDouble.html)