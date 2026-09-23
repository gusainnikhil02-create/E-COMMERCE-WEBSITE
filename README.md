import sqlite3
from flask import Flask, request, jsonify
from flask import Flask, request, jsonify, send_from_directory
from flask_cors import CORS
from werkzeug.security import generate_password_hash, check_password_hash
app = Flask(__name__)
CORS(app)
DB_FILE = 'database.db'
INITIAL_PRODUCTS = [
    {
        "name": "Onyx Silk Shirt",
        "category": "Men",
        "price": 120.00,
        "image": "https://images.unsplash.com/photo-1596755094514-f87e32f85e23?q=80&w=1976&auto=format&fit=crop",
        "description": "Experience the ultimate comfort and luxury with our Onyx Silk Shirt. Carefully crafted from 100% pure silk, this shirt features a relaxed fit perfect for evening wear or high-end casual outings.",
        "rating": 4.8,
        "review_count": 124
    },
    {
        "name": "Ivory Knit Sweater",
        "category": "Women",
        "price": 185.00,
        "image": "https://images.unsplash.com/photo-1576566588028-4147f3842f27?q=80&w=1964&auto=format&fit=crop",
        "description": "A staple for any minimalist wardrobe. The Ivory Knit Sweater is made from premium Merino wool, providing warmth without bulk. Its timeless design ensures it pairs well with any outfit.",
        "rating": 4.5,
        "review_count": 89
    },
    {
        "name": "Midnight Trench Coat",
        "category": "Men",
        "price": 340.00,
        "image": "https://images.unsplash.com/photo-1520975954732-57dd22299614?q=80&w=1974&auto=format&fit=crop",
        "description": "Brave the elements in style. Our Midnight Trench Coat offers a sleek silhouette with water-resistant fabric, making it a perfect companion for the urban explorer.",
        "rating": 5.0,
        "review_count": 42
    },
    {
        "name": "Essence Slip Dress",
        "category": "Women",
        "price": 150.00,
        "image": "https://images.unsplash.com/photo-1595777457583-95e059d581b8?q=80&w=1983&auto=format&fit=crop",
        "description": "The Essence Slip Dress embodies elegance. With its fluid drape and subtle sheen, it's designed to flatter every figure. Perfect for formal events or elevated everyday wear.",
        "rating": 4.7,
        "review_count": 210
