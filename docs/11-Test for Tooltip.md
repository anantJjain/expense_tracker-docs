****
## Tooltip view
Checks if the block is hovered in that case ```tooltipView``` is **true** and ```date``` is not empty thus rendering the tooltip and vice-versa
```jsx
test('Does not render tooltip when tooltipView is false', () => {
    render(<ToolTip tooltipView={false} date="01-01-2024" transactionsCount={5} />);
    const tooltip = screen.queryByText(/transactions on/i);
    expect(tooltip).not.toBeInTheDocument();
  });

test('Does not render tooltip when date is empty', () => {
    render(<ToolTip tooltipView={true} date="" transactionsCount={5} />);
    const tooltip = screen.queryByText(/transactions on/i);
    expect(tooltip).not.toBeInTheDocument();
  });
``` 

## Display based on transactions count
Check that "No Transactions" and "X Transactions" are displayed in case 0 and X transactions are respectively made on a particular day.
```jsx
test('Renders correct text for zero transactions count', () => {
    render(<ToolTip tooltipView={true} date="01-01-2024" transactionsCount={0} />);
    const tooltip = screen.getByText(/No transactions on/i);
    expect(tooltip).toBeInTheDocument();
});

test('Renders correct text for transactions count greater than zero', () => {
    render(<ToolTip tooltipView={true} date="01-01-2024" transactionsCount={5} />);
    const tooltip = screen.getByText(/5 transactions on/i);
    expect(tooltip).toBeInTheDocument();
});
```

## Date Format
Check if the format of the date shown in tooltip text is correct
```jsx
test('Formats date correctly', () => {
    render(<ToolTip tooltipView={true} date="01-01-2024" transactionsCount={5} />);
    const tooltip = screen.getByText(/January 1, 2024/i);
    expect(tooltip).toBeInTheDocument();
});
```

