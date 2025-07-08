# Table-printer
# Table-printer
const express = require('express');
const app = express();
const path = require('path');

app.set('view engine', 'ejs');
app.set('views', path.join(__dirname, 'views'));

app.use(express.urlencoded({ extended: true }));

app.get('/', (req, res) => {
    res.render('form');
});

app.post('/generate', (req, res) => {
    const tableNumber = parseInt(req.body.number);
    const length = parseInt(req.body.length);
    const table = [];

    for (let i = 1; i <= length; i++) {
        table.push({
            index: i,
            result: tableNumber * i
        });
    }

    res.render('table', { tableNumber, length, table });
});

app.listen(3000, () => {
    console.log('Server running on http://localhost:3000');
});
















