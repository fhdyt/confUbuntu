## Controller
```bash
public function add_quote()
{
	$data=$this->QuoteModel->add_quote_model();
	echo json_encode($data);
}
```

## Model
```bash
public function add_quote_model()
{
	$slug= url_title($this->input->post('quote'), 'dash', TRUE);
	$data = array(
		'QUOTE' => $this->input->post('quote'),
		'QUOTE_SLUG' => $slug,
);

$result=$this->db->insert('QUOTE',$data);
return $result;
}
```

## View
```bash

```

## Ajax
```bash
function save_quote(){
  $.ajax({
    type : "POST",
    url  : "<?php echo base_url() ?>index.php/quote/add_quote",
    dataType : "JSON",
    data : {
		quote : $('.quote').val(),
    },
    success: function(data)
    {
      $("#myModal").modal("hide");
	  quote_list();
    }
  });
}

```

