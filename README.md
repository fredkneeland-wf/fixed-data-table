Fixed Data Tables for Dart React
====================================

This repo was created to allow FaceBook's FixedDataTable react component to be used in Dart.  For the original source go to: https://github.com/facebook/fixed-data-table

Getting started
---------------

To use this repo include it in your pubspec.yaml as a git dependency

```yaml
fixed_data_table:
    git:
      url: git@github.com:fredkneeland-wf/fixed-data-table.git
      ref: 1.0.0
```


Then in your dart file import this package:

```dart
import 'package:fixed_data_table/fixed-data-table.dart';
```

Then inside of your render file include something in the form:

```
FixedDataTable({'rowHeight':rowHeight, 'rowGetter':rowGetterFunc, 'rowsCount':rowArray.length, 'width':TableWidth, 'height':TableHeight,'headerHeight':HeaderHeight,'groupHeaderHeight':GroupHeaderHeight}, [
        FixedDataTableColumnGroup({'label':'Users', 'width':650}, [
          FixedDataTableColumn({'width':col1Width,'cellRenderer': col1Input, 'dataKey':'col1Param'}),
          FixedDataTableColumn({'width':col2Width,'cellRenderer': col2Input, 'dataKey':'col2Param'})
        ]),
])
```

col1Width, col2Width, rowHeight, TableWidth, TableHeight, HeaderHeight, and GroupHeaderHeight are all numerical props

rowGetterFunc is a function that returns an object with the row data for an index i.e.

```dart
rowGetterFunc(rowIndex) {
  return rowArray[index];
}
```

rowArray is an array of objects that contain the data you want for your chart i.e.

```dart
var rowArray = [
  {
    'name':'name',
    'age':10
  },
  {
    'name2':'name2',
    'age':15
  }
];
```

col1Input and col2Input are functions that return the react component for a given row determined by dataKey i.e.

```dart
  col1Input(data) {
      return div({}, [
        data
      ]);
  }
  
  col2Input(data) {
        return div({}, [
          Input({'key':'1:${data}', 'onChange': onChangeFunc, 'type': 'radio', 'label': 'owner', 'value': '3', 'name': 'name', 'checked': false})
        ]);
    }
```

The parameter data will be rowArray[index]['col1Param'] if you only want to display the data and don't want to render a react component you can ommit the 'cellRenderer' prop.

Make sure to wrap a react component in a div as in the above examples as without it you will get an error.

If you have any questions feel free to ping me on hipchat or email me at fred.kneeland@workiva.com

License
-------

`FixedDataTable` is [BSD-licensed](https://github.com/facebook/fixed-data-table/blob/master/LICENSE). We also provide an additional [patent grant](https://github.com/facebook/fixed-data-table/blob/master/PATENTS).
