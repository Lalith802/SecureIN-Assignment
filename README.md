# SECUREIN Recipe API

A Flask-based REST API for managing and retrieving recipe data with advanced search capabilities and pagination support.

## 🚀 Features

- **Recipe Management**: Store and retrieve detailed recipe information
- **Advanced Search**: Filter recipes by multiple parameters
  - Title search
  - Cuisine type
  - Calorie range
  - Total cooking time
  - Rating filters
- **Smart Pagination**: Efficient data retrieval with page-based results
- **Nutritional Information**: Detailed nutrient data for each recipe
- **Rating Trends**: Visual indicators for recipe ratings (⬆ for ≥4.0, ⬇ for <4.0)

## 🛠 Tech Stack

- **Backend**: Python, Flask
- **Database**: MySQL
- **Additional Libraries**: 
  - `flask-cors`: Cross-Origin Resource Sharing support
  - `mysql-connector`: Database connectivity
  - `pandas`: Data processing
  - `numpy`: Numerical operations

## 📋 API Endpoints

### 1. Get Recipes
```http
GET /api/recipes?page=1&limit=10
```
Retrieves a paginated list of recipes sorted by rating.

### 2. Search Recipes
```http
GET /api/recipes/search
```
Search recipes with multiple filter options:
- `calories`: Support for >=, <=, = operations
- `title`: Partial text match
- `cuisine`: Exact cuisine type match
- `total_time`: Support for >=, <=, = operations
- `rating`: Support for >=, <=, = operations

## 🔧 Setup

1. Clone the repository
2. Install dependencies:
```bash
pip install flask flask-cors mysql-connector-python pandas numpy
```

3. Set up MySQL database:
```sql
CREATE DATABASE recipes_db;
```

4. Configure database connection in `Api_Integration.py`:
```python
host='127.0.0.1'
user='your_username'
password='your_password'
database='recipes_db'
```

5. Run the Flask application:
```bash
python Api_Integration.py
```

## 📊 Response Format

```json
{
  "status": "success",
  "query_params": {
    "page": 1,
    "limit": 10,
    "offset": 0
  },
  "pagination": {
    "total_records": 1000,
    "total_pages": 100,
    "current_page": 1,
    "per_page": 10
  },
  "message": "Showing recipes 1 to 10",
  "recipes": [...]
}
```

## 🔍 Example Queries

1. Get recipes with rating >= 4.5:
```
/api/recipes/search?rating=>=4.5
```

2. Search Italian recipes under 500 calories:
```
/api/recipes/search?cuisine=Italian&calories=<=500
```

3. Find quick recipes (under 30 minutes):
```
/api/recipes/search?total_time=<=30
```

## 📝 Data Import

The project includes a Jupyter notebook (`DataBase_Integration.ipynb`) for importing recipe data from JSON to MySQL. The notebook handles:
- Data cleaning
- NULL value handling
- Type conversions
- Batch database insertions

## ⚠️ Error Handling

The API includes comprehensive error handling for:
- Database connection issues
- Invalid query parameters
- Server errors
- Empty result sets

## 🔐 Security

- Input validation for all query parameters
- Prepared SQL statements to prevent SQL injection
- Error message sanitization

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

---

Made with ❤️ by Lalith Krishna
