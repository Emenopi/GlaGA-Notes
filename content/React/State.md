---
tags:
  - React
---
State is a property of a component that is watched to monitor change. The status of the state can then be used to trigger changes to the output.

Optimal use of state involves minimising state properties by removing redundant ones and grouping those updated simultaneously. Nesting inside state should be avoided.

State can be shared between components by passing it from the common parent component to the child components via [[Props]]. This will allow state to be preserved after the child components are destroyed and thus saved for later use

The state of child components can be reset from the parent by passing a `key`, updating the key will then force the child component to re-render

State for any particular component is preserved for as long as that component remains at the same place in the UI tree, otherwise the state is reset. Hence component [[Functions]] should not be nested.