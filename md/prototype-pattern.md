# Prototype

-
### Patterns we will cover

- Creational

  - Singleton
  - **Prototype**
  - Factory

- Structural

  - Decorator
  - Facade

- Behavioral

  - Mediator
  - Observer


-
### What does prototype pattern do?

- Creates duplicate objects (clones) from an original (prototype)
- Creates clones as exact copies, without running constructor

-
### Prototype signature in Java

- `implements Cloneable`
- Overrides `clone()` method

-
### Simple example

```Java
public class SimplePrototype implements Cloneable {

    @Override
    public Object clone()  {
        try {
            return super.clone();
        }catch(CloneNotSupportedException ex){

            System.out.println("Clone failed. Exception:\t" + ex);
        }
        return null;
    }
}
```

-
### Pitfalls

- Prototypes are shallow copies (mutable objects must be copied)
- Forgetting to call `super.clone()`
- Forgetting to implement `Cloneable`
- Prototypes with very large numbers of mutable objects

-
### Code Walkthrough Examples

- SimplePrototype - POPO (Plain Old Prototype Object -- not a real thing)
- ExpensivePrototype - an object that is slow to create but quick to clone
- ShallowCopyPrototype - A prototype with a mutable list (shallow copy)
- DeepCopyPrototype - A prototype with a mutable list (deep copy)

-
### When is it useful

- When you have objects that are expensive to instantiate
- When you need many copies of objects that are (initially) very similar
- When using a factory design pattern to mass-produce objects

-
### Resources

- [Prototype on SourceMaking](https://sourcemaking.com/design_patterns/prototype)
- A small [prototype lab](https://gist.github.com/DavidGinzberg/b9cb42c9748122146aca#file-3_prototypelab-md)
- [Prototype on Java2s](http://www.java2s.com/Tutorials/Java/Java_Design_Patterns/0050__Java_Prototype_Pattern.htm)
- [Shallow vs. Deep copy](http://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy)