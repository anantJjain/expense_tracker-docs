# JSON Data
***
To mimic transaction data for past one year an array of objects ( located at ```src/transaction.js``` ) is used where each object represent a particular transactions and has the following properties : 

## Properties of data object
***
| Key | Description |
|-|-|
|```date``` | Represents the date on which the transaction was made |
|```amount``` | Represents the amount of the transaction |
|```type```| Whether it is a debit or credit transaction |
|```time```| Represents the time at which transaction was made |
|```transaction_id```| Represents a unique id for each transaction |

## Data source and generation
***
The mock data used in the project is a prompt based AI-generated data obtained from [Mackaroo](https://www.mockaroo.com/).

```jsx
export const transactions = [
 {
  "date": "2023-01-01 8:34:37", //date is in yyyy-mm-dd format
  "amount": 3474.81,
  "type": "debit",
  "time": "9:17 pm",
  "transaction_id": 990
 },
 {
  "date": "2023-01-02 12:42:16",
  "amount": 1486.89,
  "type": "credit",
  "time": "1:34 am",
  "transaction_id": 268
 },
 {
  "date": "2023-01-02 14:51:04",
  "amount": 8182.93,
  "type": "debit",
  "time": "5:45 am",
  "transaction_id": 519
 },
```
