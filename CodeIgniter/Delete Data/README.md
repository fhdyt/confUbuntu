## Controller
```bash
public function delete_quote()
{
	$id = $this->uri->segment('3');
	$data = $this->QuoteModel->delete_model($id);
	echo json_encode($data);

}
```

## Model
```bash
public function delete_model()
{
  return $this->db->query('DELETE FROM QUOTE WHERE QUOTE_INDEX="'.$id.'"');
}
```

## View
```bash

```

## Ajax
```bash
$("tbody#zone_data").on('click','a.hapus', function()
{
  if(confirm("Hapus ?"))
  {
    delete_quote($(this).attr("id"));
  }
})

function delete_quote(id)
{
 	$.ajax({
 		type  : 'ajax',
 		url   : '<?php echo base_url() ?>index.php/quote/delete_quote/'+id,
 		async : false,
 		dataType : 'json',
 		success : function(data)
 		{
 			if (data.length === 0)
 			{
 			}
 			else
 			{
        quote_list();
 			}
 		},
     error: function(x, e) {
       alert("Gagal")
     } //end error
 	});
}
```
