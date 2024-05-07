***
### Checking if the fallback UI appears in case the data is empty 
```jsx
test("Renders 'No transactions made on this date' when data is empty and isOpen is true", () => {
    render(<TransactionDetails data={[]} isOpen={true} />);
    const noTransactionsText = screen.getByText(/No transactions made on this date/i);
    expect(noTransactonsText).toBeInTheDocument();
})
```

### Checking the element responsible for showing the number of transactions is rendered correctly
```jsx 
test("Renders correct number of transactions", () => {
    render(<TransactionDetails data={transactions} isOpen={true} />);
    const transactionCountText = screen.getByText(/Number of Transactions/i);
    expect(transactionCountText).toBeInTheDocument();
})
```
### Checking the correct signs (**+** for credit and **-** for debit) appears as expected
     Here a mock data is taken in Case-I credit amount > debit amount so sign should be plus and opposite in Case-II where debit > credit.
```jsx
 //Case-I
 test("Renders total spending sign correctly credit", () => {
    const testData = [
      { type: "debit", amount: 100 },
      { type: "credit", amount: 200 }
    ];
    render(<TransactionDetails data={testData} isOpen={true} />);
    const totalSpendingText = screen.getByTestId("total-amount-today-sign");
    expect(totalSpendingText).toHaveTextContent('+');
  });

  //Case-II  
  test("Renders total spending sign correctly debit", () => {
    const testData = [
      { type: "credit", amount: 100 },
      { type: "debit", amount: 200 }
    ];
    render(<TransactionDetails data={testData} isOpen={true} />);
    const totalSpendingText = screen.getByTestId("total-amount-today-sign");
    expect(totalSpendingText).toHaveTextContent('-');
  });
```  

### Checking the total spending amount for the day appears correctly
```jsx
 test("Renders total spending value correctly", () => {
    const testData = [
      { type: "debit", amount: 100 },
      { type: "credit", amount: 200 }
    ];
    render(<TransactionDetails data={testData} isOpen={true} />);
    const totalSpendingText = screen.getByTestId("total-amount-today-value");
    expect(totalSpendingText).toHaveTextContent('₹100.00');
  });
```  

### Checking if the arrow is red for debit and green for credit
```jsx
 test("Renders correct arrow icon based on total spending credit", () => {
    const testData = [
      { type: "credit", amount: 100 },
      { type: "debit", amount: 200 }
    ];
    render(<TransactionDetails data={testData} isOpen={true} />);
    const arrowIcon = screen.getByTestId("arrow-icon");
    expect(arrowIcon).toHaveClass("text-red-600"); // Assuming the arrow icon has a class based on the color
  });

  test("Renders correct arrow icon based on total spending debit", () => {
    const testData = [
      { type: "debit", amount: 100 },
      { type: "credit", amount: 200 }
    ];
    render(<TransactionDetails data={testData} isOpen={true} />);
    const arrowIcon = screen.getByTestId("arrow-icon");
    expect(arrowIcon).toHaveClass("text-green-500"); // Assuming the arrow icon has a class based on the color
  });
 ```

 ### Checking that the graph renders correctly
 ```jsx
  test("Renders chart correctly", () => {
    const testData = [
      { type: "debit", amount: 100 },
      { type: "credit", amount: 200 }
    ];
    render(<TransactionDetails data={testData} isOpen={true} />);
    const chart = screen.getByTestId("transaction-chart");
    expect(chart).toBeInTheDocument();
  });
 ``` 
   