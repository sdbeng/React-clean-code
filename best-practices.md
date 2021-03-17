## React - hooks

1. Conditional Rendering Only for One Condition
If you need to conditionally render something when a condition is true and not render anything when a condition is false, don’t use a ternary operator. Use the && operator instead.

```JS
import React, { useState } from 'react'

export const ConditionalRenderingWhenTrueGood = () => {
  const [showConditionalText, setShowConditionalText] = useState(false)

  const handleClick = () =>
    setShowConditionalText(showConditionalText => !showConditionalText)

  return (
    <div>
      <button onClick={handleClick}>Toggle the text</button>
      {showConditionalText && <p>The condition must be true!</p>}
    </div>
  )
}
```
2. Conditional Rendering on Either Condition
If you need to conditionally render one thing when a condition is true and render a different thing when the condition is false, use a ternary operator.

```JS
export const ConditionalRenderingGood = () => {
  const [showConditionOneText, setShowConditionOneText] = useState(false)

  const handleClick = () =>
    setShowConditionOneText(showConditionOneText => !showConditionOneText)

  return (
    <div>
      <button onClick={handleClick}>Toggle the text</button>
      {showConditionOneText ? (
        <p>The condition must be true!</p>
      ) : (
        <p>The condition must be false!</p>
      )}
    </div>
  )
}
```
3. Boolean Props
A truthy prop can be provided to a component with just the prop name without a value like this: myTruthyProp. Writing it like myTruthyProp={true} is unnecessary.
```JS
import React from 'react'

const HungryMessage = ({ isHungry }) => (
  <span>{isHungry ? 'I am hungry' : 'I am full'}</span>
)

export const BooleanPropGood = () => (
  <div>
    <span>
      <b>This person is hungry: </b>
    </span>
    <HungryMessage isHungry />
    <br />
    <span>
      <b>This person is full: </b>
    </span>
    <HungryMessage isHungry={false} />
  </div>
)
```
4. String Props
A string prop value can be provided in double-quotes without the use of curly braces or backticks.

```JS
//bad ex.
import React from 'react'

const Greeting = ({ personName }) => <p>Hi, {personName}!</p>

export const StringPropValuesBad = () => (
  <div>
    <Greeting personName={"John"} />
    <Greeting personName={'Matt'} />
    <Greeting personName={`Paul`} />
  </div>
)

//good ex.

export const StringPropValuesGood = () => (
  <div>
    <Greeting personName="John" />
    <Greeting personName="Matt" />
    <Greeting personName="Paul" />
  </div>
)
```
5. Event Handler Functions
If an event handler only takes a single argument for the Event object, you can just provide the function as the event handler like this: onChange={handleChange}. You don't need to wrap the function in an anonymous function like this: onChange={e => handleChange(e)}.
```JS
import React, { useState } from 'react'

export const UnnecessaryAnonymousFunctionsGood = () => {
  const [inputValue, setInputValue] = useState('')

  const handleChange = e => {
    setInputValue(e.target.value)
  }

  return (
    <>
      <label htmlFor="name">Name: </label>
      <input id="name" value={inputValue} onChange={handleChange} />
    </>
  )
}
```
6. Passing Components As Props
When passing a component as a prop to another component, you don’t need to wrap this passed component in a function if the component does not accept any props.
```JS
code here
```
//bad ex.
const CircleIcon = () => (
  <svg height="100" width="100">
    <circle cx="50" cy="50" r="40" stroke="black" stroke-width="3" fill="red" />
  </svg>
)

const ComponentThatAcceptsAnIcon = ({ IconComponent }) => (
  <div>
    <p>Below is the icon component prop I was given:</p>
    <IconComponent />
  </div>
)

export const UnnecessaryAnonymousFunctionComponentsBad = () => (
  <ComponentThatAcceptsAnIcon IconComponent={() => <CircleIcon />} />
)

//good ex.
import React from 'react'

const CircleIcon = () => (
  <svg height="100" width="100">
    <circle cx="50" cy="50" r="40" stroke="black" stroke-width="3" fill="red" />
  </svg>
)

const ComponentThatAcceptsAnIcon = ({ IconComponent }) => (
  <div>
    <p>Below is the icon component prop I was given:</p>
    <IconComponent />
  </div>
)

export const UnnecessaryAnonymousFunctionComponentsGood = () => (
  <ComponentThatAcceptsAnIcon IconComponent={CircleIcon} />
```JS
code here
```

```JS
code here
```

```JS
code here
```
