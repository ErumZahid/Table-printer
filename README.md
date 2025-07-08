<!DOCTYPE html>
<html>
<head>
    <title>Multiplication Table</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <center>
        <h1>Multiplication Table of <%= tableNumber %> up to <%= length %></h1>
        <table border="1" cellpadding="10">
            <% table.forEach(row => { %>
                <tr>
                    <td><%= tableNumber %> x <%= row.index %> = <%= row.result %></td>
                </tr>
            <% }) %>
        </table>
        <br>
        <a href="/">Generate Another</a>
    </center>
</body>
</html>




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
















