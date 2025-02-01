# Django eCommerce Website for Dropshipping

### Prerequisites
Make sure you have Python and Django installed. If not, install them using:
```bash
pip install django
```

### 1. Create a Django Project
Start by creating a new Django project.

```bash
django-admin startproject dropship_site
cd dropship_site
```

### 2. Create an App
Create a Django app where you will build the eCommerce functionalities.

```bash
python manage.py startapp store
```

### 3. Set Up Models for Products
In `store/models.py`, define models for `Product`, `Category`, and `Order`.

```python
from django.db import models

class Category(models.Model):
    name = models.CharField(max_length=255)

    def __str__(self):
        return self.name

class Product(models.Model):
    name = models.CharField(max_length=255)
    category = models.ForeignKey(Category, on_delete=models.CASCADE)
    description = models.TextField()
    price = models.DecimalField(max_digits=10, decimal_places=2)
    stock = models.IntegerField()
    image = models.ImageField(upload_to='products/')

    def __str__(self):
        return self.name

class Order(models.Model):
    product = models.ForeignKey(Product, on_delete=models.CASCADE)
    quantity = models.IntegerField()
    total_price = models.DecimalField(max_digits=10, decimal_places=2)
    date_ordered = models.DateTimeField(auto_now_add=True)
    customer_name = models.CharField(max_length=255)
    customer_address = models.TextField()
    shipped = models.BooleanField(default=False)
```

### 4. Admin Configuration
Register these models in the Django admin by editing `store/admin.py`:

```python
from django.contrib import admin
from .models import Category, Product, Order

admin.site.register(Category)
admin.site.register(Product)
admin.site.register(Order)
```

### 5. Create Views and Templates
Now create views to display the products, handle orders, and manage the cart.

In `store/views.py`:

```python
from django.shortcuts import render, get_object_or_404
from .models import Product, Order

def product_list(request):
    products = Product.objects.all()
    return render(request, 'store/product_list.html', {'products': products})

def product_detail(request, pk):
    product = get_object_or_404(Product, pk=pk)
    return render(request, 'store/product_detail.html', {'product': product})

def place_order(request, pk):
    product = get_object_or_404(Product, pk=pk)
    if request.method == 'POST':
        quantity = int(request.POST['quantity'])
        total_price = quantity * product.price
        order = Order.objects.create(product=product, quantity=quantity, total_price=total_price, customer_name=request.POST['name'], customer_address=request.POST['address'])
        order.save()
        return render(request, 'store/order_success.html', {'order': order})
    return render(request, 'store/place_order.html', {'product': product})
```

### 6. Templates
Create templates to render the views for product listing, product details, and placing orders. Inside the `store` app, create a `templates/store` folder, then add:

**Product List Template (`product_list.html`)**:
```html
<h1>Products</h1>
<ul>
  {% for product in products %}
    <li>
      <a href="{% url 'product_detail' product.id %}">{{ product.name }}</a> - ${{ product.price }}
    </li>
  {% endfor %}
</ul>
```

**Product Detail Template (`product_detail.html`)**:
```html
<h1>{{ product.name }}</h1>
<img src="{{ product.image.url }}" alt="{{ product.name }}">
<p>{{ product.description }}</p>
<p>Price: ${{ product.price }}</p>
<p>Stock: {{ product.stock }}</p>

<form action="{% url 'place_order' product.id %}" method="post">
  {% csrf_token %}
  <label for="quantity">Quantity:</label>
  <input type="number" id="quantity" name="quantity" min="1" max="{{ product.stock }}">
  <label for="name">Name:</label>
  <input type="text" id="name" name="name" required>
  <label for="address">Address:</label>
  <textarea id="address" name="address" required></textarea>
  <button type="submit">Order Now</button>
</form>
```

**Order Success Template (`order_success.html`)**:
```html
<h1>Order placed successfully!</h1>
<p>Thank you for your purchase, {{ order.customer_name }}!</p>
<p>Your order of {{ order.quantity }} {{ order.product.name }} will be shipped soon.</p>
```

### 7. URL Configuration
In `store/urls.py`, configure the routes:

```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.product_list, name='product_list'),
    path('product/<int:pk>/', views.product_detail, name='product_detail'),
    path('order/<int:pk>/', views.place_order, name='place_order'),
]
```

Include these URLs in the main `dropship_site/urls.py`:

```python
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('store.urls')),
]
```

### 8. Static and Media Files
To handle product images, set up static and media configurations in `settings.py`:

```python
# settings.py
import os

# Static files (CSS, JavaScript, Images)
STATIC_URL = '/static/'

# Media files
MEDIA_URL = '/media/'
MEDIA_ROOT = os.path.join(BASE_DIR, 'media')
```

Then, update the `urls.py` to serve media files in development:

```python
from django.conf import settings
from django.conf.urls.static import static

urlpatterns += static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
```

### 9. Migrations and Superuser
Run the following commands to apply migrations and create an admin superuser:

```bash
python manage.py makemigrations
python manage.py migrate
python manage.py createsuperuser
```

### 10. Run the Development Server
Start the server to view your eCommerce site.

```bash
python manage.py runserver
```

You can now access the website at `http://127.0.0.1:8000/`!
