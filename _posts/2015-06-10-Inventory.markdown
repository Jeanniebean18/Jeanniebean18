---
layout: post
title:  "Inventory Management Program for fictional store, Fiber's Home Store!"
date:   2015-06-17 09:10:34
categories: ruby sql coding new-coder 
---
##Inventory Managment Program

The inventory management program functions to store information on all products at Fibers Home store. The user is able to add, edit and sort products.These products are stored in a table in the SQL database. Products have 5 attributes that are stored into the table: name, brand, category ID, quantity and location ID. Category and Location ID are foreign keys from other tables. The purpose of this program was to allow the owner, who purchasing new product to see quantities in stock of all products in all locations. 

The program also stores two more tables in the database, Store Locations and Categories of products. Each product has a location and category assigned to it. 

###The Product Class
The Product class contains several methods that function to store, read and manipulate data in the products table. 
The method below, .add, begins by bringing in all attributes of a products as arguments of the method. It then stores the attributes into the products table, and finally it makes an object of the product in the Product class. 
```ruby
 def self.add(name, brand, category_id, quantity, location_id)
    CONNECTION.execute("INSERT INTO products (name, brand, category_id, 
    quantity, location_id) VALUES ('#{name}','#{brand}', #{category_id}, 
    #{quantity}, #{location_id});")
    
    product_id = CONNECTION.last_insert_row_id
    
    Product.new(product_id, name, brand, category_id, quantity, location_id)
  end
```
### The find method
The find method's purpose is to store product information from the products table into objects in Ruby. This makes for speedier access to the information without calling to the database everytime. 
``` ruby
  def self.find(product_id)
    @id = product_id
      
    result = CONNECTION.execute("SELECT * FROM products WHERE id = #{@id};").first
    temp_name = result["name"]
    temp_brand = result["brand"]
    temp_category_id = result["category_id"]
    temp_quantity = result["quantity"]
    temp_location_id = result["location_id"]
    
    Product.new(product_id, temp_name, temp_brand, temp_category_id, 
    temp_quantity, temp_location_id)
  
  end
  ```
### The save method
The save method is essential in bridging the gap between our objects and the table. It's really a "sync" to ensure all information is up to date and consistent in both places. 

``` ruby
 def save 
    CONNECTION.execute("UPDATE products SET name = '#{@name}', brand = '#{@brand}', 
    category_id = #{@category_id}, quantity = #{@quantity}, 
    location_id = #{@location_id} WHERE id = #{@id};")
  end
```
### Data in SQL - sort by quantity
A pretty cool featured of SQL is that it can manipulate data in it's tables. For example, in this program, the sort by quantity method allows the user to select this to see all products sorted by quantity.  This sorting is done in SQl, and then stored in an Array of objects. 

``` ruby

  def self.all_sorted_by_quantity
    results = CONNECTION.execute('SELECT * FROM products 
    ORDER BY quantity DESC;')
    results_as_objects = []
    
    results.each do |result_hash|
      results_as_objects << Product.new(result_hash["id"], 
      result_hash["name"], result_hash["brand"], 
      result_hash["category_id"], result_hash["quantity"], 
      result_hash["location_id"])
    end
    return results_as_objects
  end 
  ```
