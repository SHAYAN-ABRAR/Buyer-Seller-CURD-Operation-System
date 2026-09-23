# Buyer–Seller CRUD Operation System

A seller-side product management system built with **PHP and MySQL**. Sellers can add products with images, review them in a dashboard, update or delete entries, and search a product by ID to see its details and customer reviews without reloading the page.

![PHP](https://img.shields.io/badge/PHP-777BB4?style=flat-square&logo=php&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![XAMPP](https://img.shields.io/badge/XAMPP-FB7A24?style=flat-square&logo=xampp&logoColor=white)

| Add Product | Seller Dashboard |
| --- | --- |
| ![Add Product form](images/Screenshot%202024-09-21%20104200.png) | ![Product list with edit and delete actions](images/Screenshot%202024-09-23%20212121.png) |

## Features

- **Create:** an Add Product form with name, category, description, price, quantity, image upload and status.
- **Read:** a seller dashboard that lists every product with quantity sold, delivery status, payment status and review count.
- **Update:** an edit form to change a product's name, quantity sold and status fields.
- **Delete:** one-click removal with a confirmation dialog.
- **AJAX search:** type a product ID to load its details and customer reviews (with ratings) through `XMLHttpRequest`.
- **Two-layer validation:** JavaScript checks required fields before submitting, and PHP re-validates on the server (required fields, positive numeric price and quantity).
- **Image upload:** product photos are stored in `images/`, and their paths are saved in the database.

## Tech Stack

| Layer | Technology |
| --- | --- |
| Backend | PHP (mysqli) |
| Database | MySQL / MariaDB |
| Frontend | HTML, CSS, JavaScript (AJAX) |
| Local server | XAMPP (Apache + MySQL) |

## Project Structure

The code follows a simple MVC-style split:

```text
Buyer-Seller-CURD-Operation-System/
├── model/
│   └── mydb.php            # DB connection and all CRUD queries
├── control/
│   ├── process.php         # Validates the Add Product form, saves the image, inserts the row
│   ├── showproduct.php     # Renders the product table
│   ├── update.php          # Loads a product and saves edits
│   ├── delete.php          # Deletes a product by ID
│   └── searchcontrol.php   # AJAX endpoint: product details and reviews
├── view/
│   ├── home.php            # Add Product page
│   ├── seller.php          # Seller dashboard (list, search, edit, delete)
│   └── updateview.php      # Edit Product page
├── js/script.js            # Client-side validation and AJAX search
├── css/style.css
└── images/                 # Uploaded product images and screenshots
```

## Getting Started

1. Install [XAMPP](https://www.apachefriends.org/) and start **Apache** and **MySQL**.
2. Clone the project into your `htdocs` folder:

   ```bash
   cd C:/xampp/htdocs
   git clone https://github.com/SHAYAN-ABRAR/Buyer-Seller-CURD-Operation-System.git
   ```

3. In phpMyAdmin, create a database named **`product`** with the two tables below.
4. Open the app:
   - Add products: `http://localhost/Buyer-Seller-CURD-Operation-System/view/home.php`
   - Seller dashboard: `http://localhost/Buyer-Seller-CURD-Operation-System/view/seller.php`

Database credentials live in `model/mydb.php`. The defaults are host `localhost`, user `root`, an empty password and database `product`.

### Database Tables

**`product_reg`**: products

| Column | Purpose |
| --- | --- |
| `pid` | Product ID (primary key, auto-increment) |
| `pname`, `pcategory`, `pdescription` | Product details |
| `price`, `pquantity` | Price and stock quantity |
| `pimage` | Path to the uploaded image |
| `pstatus` | Active / Inactive |
| `quantity_sold`, `delivery_status`, `payment_status`, `reviews` | Sales and order info shown on the dashboard |

**`customer`**: reviews

| Column | Purpose |
| --- | --- |
| `cid` | Customer ID |
| `pid` | Reviewed product (matches `product_reg.pid`) |
| `review`, `rating` | Review text and rating out of 5 |

## Notes

This is an academic project built for learning server-side PHP. Before using it anywhere beyond localhost, switch the queries to prepared statements and add authentication.

## Author

**Shayan Abrar** · [GitHub](https://github.com/SHAYAN-ABRAR) · [LinkedIn](https://www.linkedin.com/in/shayan-abrar/) · [Portfolio](https://shayan-abrar.vercel.app)
