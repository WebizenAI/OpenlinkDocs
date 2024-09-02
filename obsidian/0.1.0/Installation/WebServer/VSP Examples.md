### 3.12.1. Simple HTML FORM usage

We will start with a small example that shows a page that constitutes a FORM with data from the user being sent when a submit button is pressed and then examine the elements and attributes that are important to us at this stage.

Consider the following piece of HTML:

```HTML
<HTML>
  <HEAD>
    <TITLE>Simple FORM demo</TITLE>
  </HEAD>
  <BODY>
  <FORM METHOD="POST" ACTION="formdemo_receiver.vsp">
    <P>Test form, type some info and click Submit</P>
    <INPUT TYPE="TEXT" NAME="myInput" />
    <INPUT TYPE="SUBMIT" NAME="submit" VALUE="Submit" />
  </FORM>
  </BODY>
</HTML>
```

All elements contained in the FORM tag are associated with that form. This is how the data and the submit button know what to do next, and which data to send, by the attributes of the FORM tag.

The METHOD attribute of the FORM TAG can be either GET or POST. The GET method allows the form submission to be contained completely in a URL which can be advantageous in that it permits bookmarking in browsers, but it also prevents form data from containing non-ASCII characters and restricts the amount of form data that can be handled. The get method is limited by the maximum length of the URL that the server and browser can process. To be safe, any form whose input might contain non-ASCII characters or more than 100 characters should use METHOD="POST".

With the POST method, the form input is submitted as an HTTP POST request with the form data sent in the body of the request. Most current browsers are unable to bookmark POST requests, but POST does not entail the character encoding and length restrictions imposed by GET.

The ACTION attribute of FORM specifies the URI of the form handler. This will usually be another web page that performs some action based on the data that is sent from the originating form. The URI could point to the same page as the data originated and for pages that perform a well defined small set of functions it usually does. When a page needs to manage multiple states there needs to be some flow control that can determine how the page was reached whether it arrived as a result of someone clicking on the submit button or it is the first time the page has been visited.

Now we will add some VSP to check the values of the parameters in the form. VSP markup is typically contained in <?vsp ... VSP ... ?> blocks.

```HTML
<HTML>
  <HEAD>
    <TITLE>Simple FORM demo</TITLE>
  </HEAD>
  <BODY>
  <P>Last value sent:</P>

  <?vsp
    http(get_keyword('myInput', params, 'no value'));
   ?>

  <FORM METHOD="POST" ACTION="formdemo.vsp">
    <P>Test form, type some info and click Submit</P>
    <INPUT TYPE="TEXT" NAME="myInput" />
    <INPUT TYPE="SUBMIT" NAME="submit" VALUE="Submit" />
  </FORM>
  </BODY>
</HTML>
```

This is the same example as above that now uses the same page for the form handler and displays the parameters each time. The first time you click the button will take you to the same page and will display whatever you typed in the field last time.

The VSP block uses two functions nested. The http function allows you to send data to the HTTP client, the browser. What we send to the browser is the result of the get_keyword function. The get_keyword function has 3 parameters, it searches for the keyword-value pair (keyword=value) where keyword matches the first parameter (in this case 'myInput') in array passed in the second parameter, and returns the value if one is found otherwise will return the 3rd parameter in the function 'no value'. The params array is a special array that contains all page parameters.

Now we will extend this further to add some conditional control so that if a value was entered we can respond directly to it. We will also use a variable this time, which must be declared first.

```HTML
<HTML>
  <HEAD>
    <TITLE>Simple FORM demo</TITLE>
  </HEAD>
  <BODY>

  <?vsp
	declare _myInput varchar;

	_myInput := get_keyword('myInput', params, 'no value');

    if (_myInput <> 'no value')
	{	http('<P>Hello, ');
		http(_myInput);
		http('</P>');
	}
	else
	{	http('<P>Please enter you name</P>');
	}
   ?>

  <FORM METHOD="POST" ACTION="formdemo.vsp">
    <P>Test form, type some info and click Submit</P>
    <INPUT TYPE="TEXT" NAME="myInput" />
    <INPUT TYPE="SUBMIT" NAME="submit" VALUE="Submit" />
  </FORM>
  </BODY>
</HTML>
```

We will now extend this even further to control the whole contents of the page. In this example we will see that VSP and HTML can be interleaved.

```HTML

<HTML>
  <HEAD>
    <TITLE>Simple FORM demo</TITLE>
  </HEAD>
  <BODY>

  <?vsp
	declare _myInput varchar;
	declare Mode varchar;

	_myInput := get_keyword('myInput', params, 'no value');
	Mode := get_keyword('submit', params, '');

    if (Mode = 'submit')
	{
   ?>

    <P>Hello, <?vsp http(_myInput); ?>
	</P>

  <?vsp
	}
	  else
	{
   ?>

  <P>Please enter you name</P>
  <FORM METHOD="POST" ACTION="formdemo.vsp">
    <INPUT TYPE="TEXT" NAME="myInput" />
    <INPUT TYPE="SUBMIT" NAME="submit" VALUE="Submit" />
  </FORM>

  <?vsp
    }
  ?>

  </BODY>
</HTML>

```
### 3.12.2. Manipulating Database Data in VSP

The following example demonstrates a basic page that has form based flow control, takes input from the user to put into the database and then displays the results. This simple example can be extended to perform more substantial operations by adding a few more inputs, buttons and states.

Things to look at:

|                                                                                                                  |
| ---------------------------------------------------------------------------------------------------------------- |
| get_keyword is used to extract parameters from the form that were posted last time                               |
| the current mode is determined by the value of the submit parameter                                              |
| straight HTML can be inline with VSP flow control which is how the whole page is contained in an _if_ condition. |

```HTML
<HTML>
<HEAD></HEAD>
<BODY>
<form method="POST" action="simpletest.vsp">

<?vsp
-- assumes that you have a table db..test_table(txt varchar(2000))

-- declare variables for use
declare _mode varchar;
declare _theValue varchar;
declare _stmt varchar;

-- get the current mode and continue accordingly
_mode := get_keyword ('submit', params, 'default');

if (_mode = 'Submit')
{
  -- if a submit was detected then insert the value into the DB
  _theValue := get_keyword('myTxtBox', params, 'no comment');
  _stmt := sprintf('insert into db..test_table(txt) values(\'%s\')', _theValue);
  exec (_stmt, '', '', '', '', '', '');

?>
   <P>Thank you for your submission.</P>
<?vsp
} else {
?>
   <DIV>
   <DIV>Simple test form, enter some text and hit submit.</DIV>
   <DIV><textarea name="other" rows="3" cols="64"></textarea></DIV>
   </DIV>

   <DIV><input type="submit" name="submit" value="Submit"></DIV>

   <HR />
   <H2>Values currently in table</H2>
   <TABLE>
   <?vsp
   for (select txt from db..test_table) do
     http(sprintf('<TR><TD>%s</TD></TR>', txt));
   ?>
   </TABLE>

<?vsp
}
?>
</form>
</BODY>
</HTML>
```
You may wish to offload some of the functionality of the page to a stored procedure and call that from that page. You may do this to improve readability of the page or there may be a series of functions that you repeat such as displaying a particular table in some format.

You could used a procedure as follows:

```HTML
create procedure table_list()
{
   http('<H2>Values currently in table</H2>');
   http('<TABLE>');
   for (select txt from db..test_table) do
      http(sprintf('<TR><TD>%s</TD></TR>', txt));
   http('</TABLE>');
};
```

You could then call this in instead of defining the query and table layout as above.

The aspects of VSP are explained in more detail in the following sections.

### 3.12.3. Simple Tutorial

The following example prints the result from executing explain:

```HTML

<?vsp
  declare meta, data any;
  exec ('explain (?)', null, null, vector ('select * from sys_users'),  0, meta, data);
  foreach (any row in data) do
  {
     http_value (row[0], 'p');
  }
?>
```
The vsp can be also written like this:

```HTML
<?vsp
  declare meta, data any;
  exec ('explain (?)', null, null, vector ('select * from sys_users'), 0, meta, data);
  for (declare i,l int, i := 0, l := length (data); i < l; i := i + 1)
   {
     http_value (data[i][0], 'p');
   }

?>
```