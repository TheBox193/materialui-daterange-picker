# materialui-daterange-picker

A react date range picker using material-ui components.

<a href='https://www.npmjs.com/package/material-mui-date-range-picker'>
    <img src='https://img.shields.io/npm/v/material-mui-date-range-picker.svg' alt='Latest npm version'>
</a>

### Forked from [jungsoft/materialui-daterange-picker](https://github.com/jungsoft/materialui-daterange-picker), [flippingbitss/react-daterange-picker](https://github.com/flippingbitss/react-daterange-picker) to work with mui v5

## Live Demo: https://nikhilgoud.github.io/material-mui-date-range-picker/

## Usage

```bash
npm install material-mui-date-range-picker --save
# or with yarn
yarn add material-mui-date-range-picker
```

![Screenshot](/screenshot.png?raw=true 'Screenshot')

## Basic Example

```tsx
import React from 'react';
import { DateRangePicker, DateRange } from 'material-mui-date-range-picker';

type Props = {};
type State = {
  open: boolean;
  dateRange: DateRange;
};

class App extends React.Component<Props, State> {
  state = {
    open: true,
    dateRange: {},
  };

  render() {
    return <DateRangePicker open={this.state.open} onChange={(range) => this.setState({ dateRange: range })} />;
  }
}

export default App;
```

## Basic example using hooks

```tsx
import React from 'react';
import './App.css';
import { DateRange, DateRangeEditor } from 'material-mui-date-range-picker';
import { ThemeProvider, StyledEngineProvider, useTheme } from '@mui/material/styles';

function App() {
  const [dateRange, setDateRange] = React.useState<DateRange>({});
  const theme = useTheme();

  return (
    <StyledEngineProvider injectFirst>
      <ThemeProvider theme={theme}>
        <div className='App'>
          <DateRangeEditor dateRange={dateRange} onChange={(range) => setDateRange(range)} />
        </div>
      </ThemeProvider>
    </StyledEngineProvider>
  );
}

export default App;
```

```tsx
import React from 'react';
import { DateRangePicker, DateRange } from 'material-mui-date-range-picker';
import { ThemeProvider, StyledEngineProvider, useTheme } from '@mui/material/styles';
type Props = {};

const App: React.FunctionComponent<Props> = (props) => {
  const [dateRange, setDateRange] = React.useState<DateRange>({});
  const [openPicker, setOpenPicker] = React.useState<boolean>(true);

  const theme = useTheme();
  const togglePicker = () => setOpenPicker(!openPicker);

  return (
    <StyledEngineProvider injectFirst>
      <ThemeProvider theme={theme}>
        <div className='App'>
          <DateRangePicker open={openPicker} toggle={togglePicker} initialDateRange={dateRange} onChange={(range) => setDateRange(range)} />
        </div>
      </ThemeProvider>
    </StyledEngineProvider>
  );
};

export default App;
```

## Types

```ts
interface DateRange {
  startDate?: Date;
  endDate?: Date;
}

interface DefinedRange {
  label: string;
  startDate: Date;
  endDate: Date;
}
```

## Props

### `DateRangePicker` Props

| Name                  | Type                  | Required   | Default value     | Description                                                           |
| :-------------------- | :-------------------- | :--------- | :---------------- | :-------------------------------------------------------------------- |
| `onChange`            | `(DateRange) => void` | _required_ | -                 | handler function for providing selected date range                    |
| `toggle`              | `() => void`          | _required_ | -                 | function to show / hide the DateRangePicker                           |
| `initialDateRange`    | `DateRange`           | _optional_ | `{}`              | initially selected date range                                         |
| `minDate`             | `Date` or `string`    | _optional_ | 10 years ago      | min date allowed in range                                             |
| `maxDate`             | `Date` or `string`    | _optional_ | 10 years from now | max date allowed in range                                             |
| `definedRanges`       | `DefinedRange[]`      | _optional_ | -                 | custom defined ranges to show in the list                             |
| `closeOnClickOutside` | `boolean`             | _optional_ | `true`            | defines if DateRangePicker will be closed when clicking outside of it |
| `wrapperClassName`    | `object`              | _optional_ | `undefined`       | defines additional wrapper style classes                              |



### `DateRangeEditor` Props

| Name                 | Type                  | Required   | Default value     | Description                                           |
| :------------------- | :-------------------- | :--------- | :---------------- | :---------------------------------------------------- |
| `dateRange`          | `DateRange`           | _required_ | `{}`              | selected date range                                   |
| `onChange`           | `(DateRange) => void` | _required_ | -                 | handler function for providing selected date range    |
| `mask`               | `string`              | _optional_ | `__/__/____`      | input mask for DateInputs                             |
| `dateInputDelimeter` | `string`              | _optional_ | `/`               | input delimeter/seperatot for DateInputs (mm/dd/yyyy) |
| `minDate`            | `Date` or `string`    | _optional_ | 10 years ago      | min date allowed in range                             |
| `maxDate`            | `Date` or `string`    | _optional_ | 10 years from now | max date allowed in range                             |
| `definedRanges`      | `DefinedRange[]`      | _optional_ | -                 | custom defined ranges to show in the list             |

_Note:_ only supports `mm/dd/yyyy` fomat as of now.
