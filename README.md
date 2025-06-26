va-marketing-agency/
├── client/
│   ├── public/
│   │   └── index.html
│   ├── src/
│   │   ├── components/
│   │   │   ├── Header.jsx
│   │   │   ├── PricingCard.jsx
│   │   │   └── Footer.jsx
│   │   ├── pages/
│   │   │   ├── Home.jsx
│   │   │   └── Pricing.jsx
│   │   ├── App.js
│   │   ├── firebase.js
│   │   └── index.js
│   └── package.json
├── server/
│   ├── routes/
│   │   ├── auth.js
│   │   └── payments.js
│   ├── server.js
│   └── package.json
└── .gitignore
{
  "name": "va-marketing-client",
  "version": "1.0.0",
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build"
  },
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-router-dom": "^6.14.2",
    "firebase": "^10.5.0",
    "@stripe/stripe-js": "^3.1.0"
  }
}const express = require('express');
const cors = require('cors');
const app = express();

app.use(cors());
app.use(express.json());

// Auth routes
app.use('/auth', require('./routes/auth'));

// Payment routes
app.use('/payments', require('./routes/payments'));

const PORT = 5000;
app.listen(PORT, () => console.log(`Server running on port ${PORT}`));
import { BrowserRouter, Routes, Route } from 'react-router-dom';
import Home from './pages/Home';
import Pricing from './pages/Pricing';

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/pricing" element={<Pricing />} />
      </Routes>
    </BrowserRouter>
  );
}

export default App;
