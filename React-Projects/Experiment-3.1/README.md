ProductCard Component Using Props – Experiment-7

🎯 Objective

Build a reusable React component that displays product details using props and a separate header component.
This task helps you understand props, component reusability, and clean project structure in React.

---

📝 Task Description

Create:

ProductCard → Displays product details (name, price, status)

ProductList → Stores product data and renders multiple ProductCards

Header → Displays page title

## App.js → Combines everything together

📂 Project Structure
src/
┣ components/
┃ ┣ Header.js
┃ ┣ ProductCard.js
┃ ┗ ProductList.js
┣ App.js
┣ App.css
┗ index.js

---

🛠 Step-by-Step Implementation
Step 1: Create Header.js

const Header = ({ title }) => {
return <h2 className="header">{title}</h2>;
};

export default Header;

Explanation:

Header is a reusable component that takes a title as a prop and displays it.

## This helps you keep headings consistent across the app.

Step 2: Create ProductCard.js
import React from "react";
import "../App.css";

const ProductCard = ({ name, price, status }) => {
return (

<div className="product-card">
<h3>{name}</h3>
<p>Price: ${price}</p>
<p>Status: {status}</p>
</div>
);
};

export default ProductCard;

Explanation:

ProductCard receives props and displays product details inside a styled card.

## This is fully reusable for any product.

Step 3: Create ProductList.js
import React from "react";
import ProductCard from "./ProductCard";
import Header from "./Header";
import "../App.css";

const ProductList = () => {
const products = [
{ name: "Wireless Mouse", price: 25.99, status: "In Stock" },
{ name: "Keyboard", price: 45.5, status: "Out of Stock" },
{ name: "Monitor", price: 199.99, status: "In Stock" }
];

return (

<div className="product-list">
<Header title="Products List" />
<div className="product-container">
{products.map((item, index) => (
<ProductCard
            key={index}
            name={item.name}
            price={item.price}
            status={item.status}
          />
))}
</div>
</div>
);
};

export default ProductList;

Explanation:

Added Header to display the page title.

## Looped over product array using .map() to dynamically render multiple cards.

Step 4: Update App.js
import React from "react";
import ProductList from "./components/ProductList";
import "./App.css";

function App() {
return (

<div className="App">
<ProductList />
</div>
);
}

export default App;

Explanation:

## Root component renders only ProductList keeping the app clean and modular.

Step 5: Add Styles in App.css
.App {
text-align: center;
padding: 20px;
}

.header {
font-size: 1.8rem;
margin-bottom: 20px;
text-decoration: underline;
}

.product-container {
display: flex;
gap: 15px;
justify-content: center;
flex-wrap: wrap;
}

.product-card {
border: 1px solid #ccc;
border-radius: 10px;
padding: 15px;
width: 200px;
box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
text-align: center;
background-color: #fafafa;
}

Explanation:

Added .header for title styling.

Used flexbox in .product-container for responsive layout.

## Styled .product-card to look like individual boxes.

📚 Learning Outcomes

✅ Props : Understand how to pass and use props in React.
✅ Reusable Components: Learn to create separate, modular components.
✅ Dynamic Rendering: Use .map() to generate multiple components from data.
✅ Clean UI: Organize project structure for readability and maintainability.
✅ Styling Best Practices: Use CSS classes instead of inline styles.

