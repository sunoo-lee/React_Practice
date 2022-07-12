import { useState, useEffect } from "react";

function App() {
  const [loading, setLoading] = useState(true);
  const [coins, setCoins] = useState([]);
  const [cash, setCash] = useState(0);
  const [price, setPrice] = useState(0);
  useEffect(() => {
    fetch("https://api.coinpaprika.com/v1/tickers")
      .then((response) => response.json())
      .then((json) => {
        setCoins(json);
        setLoading(false);
      });
  }, []);

  const onChange = (event) => setCash(event.target.value);
  const onSelect = (event) => setPrice(event.target.value);

  return (
    <div className="App">
      <h1>The Coins ({coins.length}) </h1>
      {loading ? <strong>Loading...</strong> : null}
      <br />
      <span>Your Cash: </span>
      <input
        value={cash}
        onChange={onChange}
        type="number"
        placeholder="Type here..."
      />
      <span> USD</span>
      <br />
      <span>Select Coin: </span>
      <select onChange={onSelect}>
        {coins.map((coin, index) => (
          <option value={coin.quotes.USD.price} key={index}>
            {/* {coin.name} ({coin.symbol}) */}
            {coin.name} ({coin.symbol})
          </option>
        ))}
      </select>
      <br />
      <span>You can buy: </span>
      <input value={cash / price} type="number" disabled={true} />
      <hr />
    </div>
  );
}

export default App;
