https://docs.openlinksw.com/virtuoso/qstpublishbifs/

### 3.7.3. Publishing VSE's as Web Services

The Virtuoso distribution includes the sample VSE, bif_sample.c. It is thus possible to create a function such as:

.....
static caddr_t
bif_hello_world (caddr_t * qst, caddr_t * err_ret, state_slot_t ** args)
{
  return box_dv_short_string ("Hello world.");
}
....

Then declare it in the init_func() by adding the following code:

...
  bif_define_typed ("hello_world", bif_hello_world, &bt_any);
...

The next step is creating a stored procedure that calls this function and you are back to publishing a Virtuoso stored procedure again, as in the above section.

create procedure BIF_HELLO_WORLD () { return hello_world (); };

|   |   |
|---|---|
|![[Tip]](https://docs.openlinksw.com/virtuoso/qstpublishbifs/images/tip.png)|See Also:|
|The [C Interface](https://docs.openlinksw.com/virtuoso/cinterface/) Chapter|