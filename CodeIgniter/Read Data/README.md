## Controller
```bash
public function quote_list()
{
	$data=$this->QuoteModel->quote_list_model();
	echo json_encode($data);
}

```

## Model
```bash
public function quote_list_model()
{
  $hasil=$this->db->query('SELECT * FROM QUOTE')->result();
  return $hasil;
}
```

## View
```bash
<table class="table table-bordered">
  <thead>
    <tr>
      <th>No.</th>
      <th>Quote</th>
      <th>Slug</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody id="zone_data">
    <tr>
      <td colspan="9">
        <center>
          <div class="loader"></div>
        </center>
      </td>
    </tr>
  </tbody>
</table>

```

## Ajax
```bash
$(function()
{
  quote_list();
});

function quote_list()
{
	$.ajax({
		type  : 'ajax',
		url   : "<?php echo base_url() ?>index.php/quote/quote_list",
		async : false,
		dataType : 'json',
		success : function(data)
		{
			$("tbody#zone_data").empty();
			if (data.length === 0)
			{
			}
			else
			{
				var no = 1
				for (i = 0; i < data.length; i++) {
					$("tbody#zone_data").append("<tr>" +
					"<td >" + no++ +"</td>" +
					"<td >" + data[i].QUOTE + "</td>" +
					"<td >" + data[i].QUOTE_SLUG + "</td>" +
					"<td><a class='btn btn-danger btn-sm hapus' id='" + data[i].QUOTE_INDEX + "'><i class='fas fa-trash'></i></a></td>" +
					"<td><a class='btn btn-primary btn-sm copy' texttocopy='"+data[i].QUOTE+"'><i class='fas fa-copy'></i></a></td>" +
					"</tr>");
				}
			}
		},
		error: function(x, e) {
			console.log("Gagal")
		}
	});
}
```
