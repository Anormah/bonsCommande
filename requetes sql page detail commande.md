Sur la page d'accueil créer un lien ayant comme paramètre le numéro de la commande
Cela nous permettra d'arriver sur une page de détails de la commande



Récupération du client

SELECT
    customerName,
    contactFirstName,
    contactLastName,
    addressLine1,
    addressLine2,
    city
    FROM customers
    INNER JOIN orders ON orders.customerNumber = customers.customerNumber
    WHERE orderNumber = ?



Récupération des lignes de la commande

SELECT
    productName,
    priceEach,
    quantityOrdered,
    priceEach * quantityOrdered AS totalPrice
    FROM orderdetails
    INNER JOIN products ON products.productCode = orderdetails.productCode
    WHERE orderNumber = ?
    ORDER BY orderLineNumber


Récupération du montant total 

SELECT SUM(priceEach * quantityOrdered) AS totalAmount
    FROM orderdetails
    WHERE orderNumber = ?