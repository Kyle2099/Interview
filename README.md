# Interview

Three examples of work/projects that you've recently participated in...

1)

Tic-Tac-Toe


This code is how I created a tic-tac-toe game in react.

```javascript
function Square(props) {
  return (
    <button className="square" data-pro={props.value} onClick={props.onClick}>
      {props.value}
    </button>
  );
}



// class initialize extends React.Component {

// }

class Board extends React.Component {
  renderSquare(i) {
    return (
      <Square
        value={this.props.squares[i]}
        onClick={() => this.props.onClick(i)}
      />
    );
  }

  render() {            
    return (
      <div>
        <div className="board-row">
          {this.renderSquare(0)}
          {this.renderSquare(1)}
          {this.renderSquare(2)}
        </div>
        <div className="board-row">
          {this.renderSquare(3)}
          {this.renderSquare(4)}
          {this.renderSquare(5)}
        </div>
        <div className="board-row">
          {this.renderSquare(6)}
          {this.renderSquare(7)}
          {this.renderSquare(8)}
        </div>
      </div>
    );
  }
}

class Game extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      history: [
        {
          squares: Array(9).fill(null)
        }
      ],
      stepNumber: 0,
      xIsNext: true
    };
  }

  handleClick(i) {
    const history = this.state.history.slice(0, this.state.stepNumber + 1);
    const current = history[history.length - 1];
    const squares = current.squares.slice();
    if (calculateWinner(squares) || squares[i]) {
      return;
    }
    squares[i] = this.state.xIsNext ? "X" : "O";
    this.setState({
      history: history.concat([
        {
          squares: squares
        }
      ]),
      stepNumber: history.length,
      xIsNext: !this.state.xIsNext
    });
  }

  jumpTo(step) {
    this.setState({
      stepNumber: step,
      xIsNext: (step % 2) === 0
    });
  }

  render() {
    const history = this.state.history;
    const current = history[this.state.stepNumber];
    const winner = calculateWinner(current.squares);


    const moves = history.map((step, move) => {
      const desc = move ?
        'Go to move #' + move :
        'Click to start a new game';
      return (
        <li key={move}>
          <button onClick={() => this.jumpTo(move)}>{desc}</button>
        </li>
      );
    });

    let status;
    if (winner) {
      status = "Winner: " + winner;
    } else {
      status = "Next player: " + (this.state.xIsNext ? "X" : "O");
    }

    return (
      <div class="a">
        <h1>
          Tic-Tac-Toe!
        </h1>

        <div className="game">
          <div className="game-board">
            <Board
              squares={current.squares}
              onClick={i => this.handleClick(i)}
            />
          </div>
          <div className="game-info">
            <div>{status}</div>
            <ol>{moves}</ol>
          </div>
        </div>
      </div>

    );
  }
}

// ========================================

ReactDOM.render(<Game />, document.getElementById("root"));

function calculateWinner(squares) {
  const lines = [
    [0, 1, 2],
    [3, 4, 5],
    [6, 7, 8],
    [0, 3, 6],
    [1, 4, 7],
    [2, 5, 8],
    [0, 4, 8],
    [2, 4, 6]
  ];
  for (let i = 0; i < lines.length; i++) {
    const [a, b, c] = lines[i];
    if (squares[a] && squares[a] === squares[b] && squares[a] === squares[c]) {
      return squares[a];
    }
  }
  return null;
}


serviceWorker.unregister();
```

2)


Bamazon -

In this application I have created an Amazon-like storefront with the MySQL skills that I have learned. The app will take in orders from customers and deplete stock from the store's inventory. I have you programed the app to track product sales across your store's departments and then provide a summary of the highest-grossing departments in the store.

This is a CLI application. The application can be found at https://github.com/Kyle2099/bamazon

 The Customer View -

The products table inside of the database stores the item_id product_name department_name price and the stock_quantity.

The application prompts users with three questions.

Please enter the Item ID which you would like to purchase.

How many do you need?

If there is not enough in stock the user will recieve this.

How many do you need? 5000 Sorry, Insufficient quantity! Please check back later. Please modify your quantity.

Would you like to continue? (Y/n)

Manager View-

There is a list of menu options

View products for sale - The app should list every available item: the item IDs, names, prices, and quantities.
View Low inventory - The app lists all items with an inventory count lower than one hundred. -Add to Inventory - The app displays a prompt that will let the manager "add more" of any item currently in the store.
Add New product - The app allows the manager to add a completely new product to the store.
The Supervisor View -

When a supervisor selects View Product Sales by Department, the app will display a summarized table in their terminal/bash window.

The total_profit column should be calculated on the fly using the difference between over_head_costs and product_sales. total_profit should not be stored in any database. But instead uses custom alias. Using GROUP BYs and JOINS.

Using npm Console.table to set up the table structure.


Link- 

https://github.com/Kyle2099/bamazon



3)

The Crystal Game-


A random number is generated at the beginning of the game. You can win the game by figuring out how to reach the random number by clicking on the crystals. Adding up the crystal your score with increase with points.The value of each crystal are hidden. We like to give you a bit of a challange.
Each time when the game begins the value of each crystal will Change.
https://kyle2099.github.io/unit-4-game/




Provide up to three examples of work that has recently inspired you from a technical perspective. 

1. https://opensource.google.com/projects/magenta
I have always been interested in TensorFlow. I have many ideas on how I could use TensorFlow. Using machine learning to learn human behaviors, understanding tone of voice and facial expressions. Allowing the machine to decipher different human emotions. 

2. https://www.sciencemag.org/news/2017/11/surfer-and-scientist-teamed-create-perfect-wave
I'm inspired by using technology to build the perfect wave. Understand how the wave breaks by the force behind the wave and by using code to generate the wave. 

3. https://opensource.google.com/projects/tensorflow-playground

TensorFlow Playground allows for in-broswer visualization of neural networks. It contains a tiny neural network library that meets the demands of this educational visualization. I really like that you can visualize in the browser how the machine is learning. 




Focus-


I would focus my time learning about machine learning and how to structure data. I want to learn more about big data and how it can be used to have a deeper understanding of where the future of tech can go. 



Code challenge -

https://codesandbox.io/s/nrxm1n46ol?fontsize=14
