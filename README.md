# NG Prime Tools

An advanced PrimeNG tools library for Angular.

## Table of Contents

- [Introduction](#introduction)
- [Installation](#installation)
- [Compatibility](#compatibility)
- [Usage](#usage)
  - [ng-advanced-prime-table](#ng-advanced-prime-table)
    - [Inputs](#inputs)
    - [Outputs](#outputs)
    - [Example](#example)
- [Changelog](#changelog)
- [License](#license)

## Introduction

`ng-prime-tools` is a collection of advanced tools built on top of PrimeNG for Angular applications.

## Installation

To install `ng-prime-tools`, use the following command:

```bash
npm install ng-prime-tools
```

## Compatibility

- **Angular Version**: 17.3.1 or higher
- **PrimeNG Version**: 17.18.0 or higher

## Usage

### ng-advanced-prime-table

To use the `ng-advanced-prime-table` component, follow these steps:

1. **Import the Module:**

   Import the `NgAdvancedPrimeTableModule` in your Angular module or standalone component.

   ```typescript
   import {
     NgAdvancedPrimeTableModule,
     TableColumn,
     TableTypeEnum,
   } from "ng-prime-tools";
   ```

2. **Add the Component:**

   Add the `ng-advanced-prime-table` component to your template:

   ```html
   <ng-advanced-prime-table
     [columns]="columns"
     [data]="data"
     [hasSearchFilter]="true"
     [hasColumnFilter]="true"
     [isPaginated]="true"
     [totalRecords]="totalRecords"
     [isSortable]="true"
   ></ng-advanced-prime-table>
   ```

3. **Define the Inputs:**

   In your component, define the necessary inputs for the table:

   ```typescript
   import { Component, OnInit } from "@angular/core";
   import { NgAdvancedPrimeTableModule } from "ng-prime-tools/ng-advanced-prime-table";
   import { TableColumn } from "ng-prime-tools/models";
   import { TableTypeEnum } from "ng-prime-tools/enums";

   @Component({
     selector: "app-root",
     standalone: true,
     imports: [NgAdvancedPrimeTableModule],
     templateUrl: "./app.component.html",
     styleUrls: ["./app.component.css"],
   })
   export class AppComponent implements OnInit {
     columns: TableColumn[] = [];
     data: any[] = [];
     totalRecords: number = 0;

     ngOnInit(): void {
       this.columns = [
         {
           title: "Name",
           code: "name",
           type: TableTypeEnum.STRING,
           isEditable: true,
         },
         {
           title: "Date",
           code: "date",
           type: TableTypeEnum.DATE,
           isEditable: true,
         },
         {
           title: "Amount",
           code: "amount",
           type: TableTypeEnum.AMOUNT,
           currency: "USD",
           isEditable: true,
         },
       ];

       this.data = [
         { name: "John Doe", date: "11/06/2024", amount: 100 },
         { name: "Jane Doe", date: "20/06/2024", amount: 200 },
       ];

       this.totalRecords = this.data.length;
     }
   }
   ```

### Inputs

- **data** (`any[]`): The data to be displayed in the table.
- **columns** (`TableColumn[]`): The columns configuration for the table.
- **totalRecords** (`number`): The total number of records.
- **rowsPerPage** (`number[]`): The number of rows per page options for pagination.
- **hasSearchFilter** (`boolean`): Whether the table has a global search filter.
- **hasColumnFilter** (`boolean`): Whether the table has column-specific filters.
- **isPaginated** (`boolean`): Whether the table is paginated.
- **actions** (`any[]`): The actions available for the table rows.
- **isSortable** (`boolean`): Whether the table columns are sortable.

### Outputs

- **filter** (`EventEmitter`): Emitted when the table is filtered.
- **search** (`EventEmitter<any>`): Emitted when a global search is performed.

### Example

Here's a complete example of how to use the `ng-advanced-prime-table` component:

```typescript
import { Component, OnInit } from "@angular/core";
import { CommonModule } from "@angular/common";
import { NgAdvancedPrimeTableModule } from "ng-prime-tools/ng-advanced-prime-table";
import { TableColumn } from "ng-prime-tools/models";
import { TableTypeEnum } from "ng-prime-tools/enums";

@Component({
  selector: "app-root",
  standalone: true,
  imports: [CommonModule, NgAdvancedPrimeTableModule],
  templateUrl: "./app.component.html",
  styleUrls: ["./app.component.css"],
})
export class AppComponent implements OnInit {
  columns: TableColumn[] = [];
  data: any[] = [];
  totalRecords: number = 0;

  ngOnInit(): void {
    this.columns = [
      {
        title: "Name",
        code: "name",
        type: TableTypeEnum.STRING,
        isEditable: true,
      },
      {
        title: "Date",
        code: "date",
        type: TableTypeEnum.DATE,
        isEditable: true,
      },
      {
        title: "Amount",
        code: "amount",
        type: TableTypeEnum.AMOUNT,
        currency: "USD",
        isEditable: true,
      },
    ];

    this.data = [
      { name: "ZAK JAAI", date: "11/06/2024", amount: 100 },
      { name: "ZAK2 JAAI", date: "20/06/2024", amount: 200 },
    ];

    this.totalRecords = this.data.length;
  }
}
```

```html
<ng-advanced-prime-table
  [columns]="columns"
  [data]="data"
  [hasSearchFilter]="true"
  [hasColumnFilter]="true"
  [isPaginated]="true"
  [totalRecords]="totalRecords"
  [isSortable]="true"
></ng-advanced-prime-table>
```

## Changelog

### Version 1.0.3

- Initial release with `ng-advanced-prime-table` component.

## License

This project is licensed under the MIT License.
