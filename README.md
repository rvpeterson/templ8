# Templ8
A really simple HTML template class for PHP

## What can you do with it?
Basically, this class enables you to load a HTML based template file, replace keywords, split the template, and output the markup

### Load a Template
When you init the class, you can specify the file you want to load, like this:

```PHP
$split = true;
$main_template = new templ8('templates/default.html',$split,$keywords);	
```

### Replace Keywords
When you init the class, you specify $keywords. This should be an array of key=> value. For example:

```PHP
$keywords = array('THISKEYWORD' => 'This value will be displayed');
```

THISKEYWORD will be usable in your HTML file as [TPL8_THISKEYWORD]

### Split the template
Splitting the template involves splitting the HTML markup into an upper and lower portion using the [TPL8_SPLIT] keyword. 
Typically you would put this keyword where you want to put the content, then output the upper template, your content and then the lower template

#### Automatically
You can split the template by specifying $split = true in the constructor.

#### Manually
It's a good idea to check if the current template is splittable, so use this variable to check:

```PHP
$main_template->_can_split;
```

Then you can manually split the template using this function

```PHP
$main_template->split_template();
```

Once the template has been automatically or manually split, you can output the template as a whole, or by outputing the top and bottom parts separately, as described in the next part.

### Output Markup
You can tell the template to output using this function:

```PHP
$main_template->output();
```

If you want to just get the markup, use:

```PHP
 $markup = $main_template->get_markup();
```

If you've split the template, you can use these functions:

```PHP
 $main_template->output_upper(); // output everything above the split keyword
 $main_template->output_lower(); // output everything below the split keyword
```

