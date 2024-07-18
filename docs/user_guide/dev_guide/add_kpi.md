# add\_KPI

## How to add a KPI in your report

1. Develop something (you can test it in the test zone)
2. When it's work add your KPI calculation in the KPI file and the KPI plot code in the KPI\_plot.py
3. Remember to do a documentation about the both method you've added
4. In Data>data\_project folder, in the KPI\_in\_report.xlsx, add the name you want for your KPI (⚠️ the name need to be the same as the name of the method in KPI\_Plot + \_plot at the end, for example: add energy\_poc, for the method energy\_poc\_plot()). Add also the category you want to add your KPI (in the KPI\_categories columns). Order matter for the PDF report.
5. Verify that your KPI is well plot in the example notebook.
6. Here it is, you added a new KPI ! Well done 🌟

## Documentation

Documentation is really important to follow the advance of a project and use it (for both internal and external users). Please follow this step to document the new KPI that you add.

### In method

Your method need also documentation. Useful when you need a fast check during the development of a tool. Please follow this template for document your new method :

```
'''
Method's summary ....

Parameters:
----------
self : self 
    General information 

parameters 1 : type
    comment of parameters 1 

parameters 2 : type
    comment of parameters 2

Returns:
----------
returns 1 : type
    comment of returns 1 

returns 2 : type
    comment of returns 2
'''
```

### In online documentation

Main documentation is on online, please add the documentation in the good pages (sorted by class) and add your method on it. Like before, please follow this template for the documentation of your new method :

```
### method name(self) :
Method's summary ..... <br/>
**Parameters:**

- `self` (self): General information

- `parameters 1` (type): Comment of parameters 1

- `parameters 2` (type): Comment of parameters 2

**Returns:**  

- `returns 1` (type) : Comment in returns 1  

- `returns 2` (type) : Comment in returns 2  

**Example:**  

Example how to use it ....
```

That give you this result in html page :

#### method name(self) :

Method's summary .....\
**Parameters:**

* `self` (self): General information
* `parameters 1` (type): Comment of parameters 1
* `parameters 2` (type): Comment of parameters 2

**Returns:**

* `returns 1` (type) : Comment in returns 1
* `returns 2` (type) : Comment in returns 2

**Example:**

```
Example how to use it ....
```
