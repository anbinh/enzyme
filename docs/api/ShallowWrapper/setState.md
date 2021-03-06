# `.setState(nextState[, callback]) => Self`

A method to invoke `setState()` on the root component instance similar to how you might in the
definition of the component, and re-renders.  This method is useful for testing your component
in hard to achieve states, however should be used sparingly. If possible, you should utilize
your component's external API (which is [accessible via `.instance()`](http://airbnb.io/enzyme/docs/api/ShallowWrapper/instance.html)) in order to get it into whatever state you want to test, in order
to be as accurate of a test as possible. This is not always practical, however.

NOTE: can only be called on a wrapper instance that is also the root instance.


#### Arguments

1. `nextState` (`Object`): An object containing new state to merge in with the current state
2. `callback` (`Function` [optional]): If provided, the callback function will be executed once setState has completed


#### Returns

`ShallowWrapper`: Returns itself.



#### Example

```jsx
class Foo extends React.Component {
  constructor(props) {
    super(props);
    this.state = { name: 'foo' };
  }

  render() {
    const { name } = this.state;
    return (
      <div className={name} />
    );
  }
}
```
```jsx
const wrapper = shallow(<Foo />);
expect(wrapper.find('.foo')).to.have.length(1);
expect(wrapper.find('.bar')).to.have.length(0);
wrapper.setState({ name: 'bar' });
expect(wrapper.find('.foo')).to.have.length(0);
expect(wrapper.find('.bar')).to.have.length(1);
```


#### Common Gotchas



#### Related Methods

- [`.setProps(props) => Self`](setProps.md)
- [`.setContext(context) => Self`](setContext.md)


