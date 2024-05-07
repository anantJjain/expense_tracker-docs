# Home
***
This components represents the landing page of the app that appears after the inital load time. 
## State variables
***
This component utilizes the ```useState()``` hook and defines the following state variables : 
| State Variable | Values | Description |
|-|-|-|
|```isOpen``` | Boolean | Whether the block is clicked or not |
|```clickedDate```| String | Stores the date of the clicked block |
|```data```| [] | An array containing all the objects with the date matching to the date of clicked block |
|```transactionsCount```| Number | Number of transactions on that day |
|```tooltipView```| Boolean | Whether block is hovered or not |
|```isLoading```| Boolean | Whether the initial loading time is over |
|```yearlyDebit```|Number| Stores the year-round debit amount |
|```yearlyCredit```|Number|Stores the year-round credit amount |
|```dateTransactions```|Number| A 53*7 2D array storing the number of transactions made on that day |
|```dateBlocks```|Number| A 53*7 2D array storing the date of the block|
|```hue```| Number| A 53*7 2D array used as h value in hsl() coloring |
|```saturation```| Number | A 53*7 2D array used as s value in hsl() coloring |
|```lightness```| Number | A 53*7 2D array used as l value in hsl() coloring |



For handling the date and time based calculations and I have used [Moment.js](https://momentjs.com/) 

## Inside the useEffect hook
***
First the ```useEffect()``` hook runs during the initial page load and runs the following functions asynchronously to set the corresponding dates,number of transactions and color intensity to each block : 
 Function | Description |
|-|-|
|[```setDateWiseTransactions()```](./04-Color%20Intensities.md#setdatewisetransactions) | Sets number of transactions corresponding to each date |
|[```setDates()```](./05-Dates.md#setdates) |  Sets corresponding dates of each block |
|[```setColor()```](./04-Color%20Intensities.md#setcolor) | Sets hsl() values of each block |
|[```calcTotalSpending()```](#calctotalspending) | Calculate the total debit and credit in last year |

## calcTotalSpending()
***
This function calculates the total debit amount and total credit amount of all the transactions made in the past 1 year and store the values in the ```yearlyDebit``` and ```yearlyCredit``` state variables respectively. 
```jsx
const calcTotalSpending = async () => {
  let sumDebit=0,sumCredit=0;
  for(let i=0;i<transactions.length;i++){
    if(transactions[i].type==="debit") sumDebit+=transactions[i].amount;
    else sumCredit+=transactions[i].amount;
  }
  return [ setYearlyDebit(sumDebit),setYearlyCredit(sumCredit) ];
}
```