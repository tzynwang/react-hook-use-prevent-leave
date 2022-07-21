# react hook: usePreventLeave

```string
npm i react-hook-use-prevent-leave
```

- A react custom hook to prompt confirm dialog when user tries to close the tab or refresh the page
- Supports TypeScript
- DEMO: https://tzynwang.github.io/react-hook-use-prevent-leave/
- NOTE: This hook will NOT block the navigation leave; to prompt a confirmation for this, use `Prompt` from `react-router-dom` (also includes in the example codes)

## Example

```tsx
import React, { useState } from 'react';
import { Prompt } from 'react-router-dom';
import usePreventLeave from 'react-hook-use-prevent-leave';

function PageShouldBeBlocked(): React.ReactElement {
  /* State */
  const [blockPage, setBlockPage] = useState<boolean>(true);

  /* Function */
  function togglePageBlock(): void {
    setBlockPage((prev) => !prev);
  }

  /* Hook */
  usePreventLeave(blockPage);
  // Or just call usePreventLeave() without passing any params, this mean the page will always be blocked.

  /* Main */
  return (
    <React.Fragment>
      <Prompt when={blockPage} message={'Confirm to leave this page?'} />
      <div>This page is {!blockPage && 'NOT'} block now.</div>
      <button onClick={togglePageBlock}>Click to toggle block or not.</button>
    </React.Fragment>
  );
}

export default PageShouldBeBlocked;

```

## Author

Charlie (Tzu Yin)\
[Blog](https://tzynwang.github.io/) | [GitHub](https://github.com/tzynwang)