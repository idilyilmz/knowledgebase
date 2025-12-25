# Vue

## Syntax

### Interpollation `{{ }}`

Vue's interpolation syntax (`{{ }}`) is a powerful feature for embedding dynamic content directly into your HTML templates. Here's what you **can** and **can't** do within the interpolation syntax.

#### What You Can Do

1. Bind Data:

Display data from your Vue component.

<p>{{ message }}</p>


If message = "Hello, World!", the output will be:

<p>Hello, World!</p>


2. Use JavaScript Expressions:

You can use simple expressions like mathematical operations, ternary operators, or method calls.

<p>{{ count + 1 }}</p>
<p>{{ isActive ? 'Active' : 'Inactive' }}</p>
<p>{{ greet('Vue') }}</p>


3. Access Computed Properties:

Interpolate values from computed properties.

<p>{{ reversedMessage }}</p>


4. Filter Data:

Apply custom filters to modify the displayed output.

<p>{{ price | currency }}</p>


5. Use Template Literals:

Leverage ES6 template strings for formatted output.

<p>{{ `Hello, ${name}!` }}</p>

#### What You Can't Do

1. Execute Statements:

You can't include control structures like if statements, for loops, or assignments.

<!-- INVALID -->
<p>{{ if (count > 10) { 'High' } }}</p>


2. Manipulate DOM Directly:

You can't use interpolation to perform DOM-related operations, like accessing elements or modifying their properties.

3. Call Asynchronous Code:

You can't call asynchronous functions or use await.

<!-- INVALID -->
<p>{{ await fetchData() }}</p>


4. Multi-Line or Complex Logic:

Interpolations are limited to single-line expressions.

<!-- INVALID -->
<p>{{ 
  const x = 5;
  x * 2;
}}</p>


5. HTML Markup Rendering:

By default, interpolation escapes HTML to prevent XSS attacks.

<p>{{ '<strong>Bold</strong>' }}</p> <!-- Output: <strong>Bold</strong> -->


To render raw HTML, use the v-html directive instead:

<p v-html="rawHtml"></p>


6. Bind Attributes or Styles:

Interpolation works only in text nodes, not in attributes or styles.

<!-- INVALID -->
<img src="{{ imageUrl }}" />


Use v-bind or its shorthand instead:

<img :src="imageUrl" />

#### Summary Table
| Feature                          | supported in `{{ }}`?   | Alternative **If Not Supported**   |
|----------------------------------|-------------------------|------------------------------------| 
| Binding simple data              | Yes                     | -                                  |
| Using JS expressions             | Yes                     | -                                  |
| Control structures (`if`, `for`) | No                      | Use `v-if`, `v-for`                |
| DOM manipulation                 | No                      | Use lifecycle hooks or methods     |
| Multi-line expressions           | No                      | Use methods or computed properties |
| HTML rendering                   | No (Escapes by default) | Use `v-html` (with caution)        |
| Attribute or style binding       | No                      | Use `v-bind`                       |
