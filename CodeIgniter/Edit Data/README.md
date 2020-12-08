## Controller
```bash
public function add_member()
{
	$data=$this->MModel->add_member_model();
	echo json_encode($data);
}
```

## Model
```bash
public function add_member_model()
{
if($this->input->post('member_id') == '')
{
  $data = array(
    'MEMBER_ID' 			=> create_id(),
    'MEMBER_NAME' 			=> $this->input->post('name'),
    'MEMBER_GENDER' 			=> $this->input->post('gender'),
    'MEMBER_ADDRESS' 			=> $this->input->post('address'),
    'MEMBER_GENDER' 			=> $this->input->post('gender'),
    'MEMBER_CONTACT' 			=> $this->input->post('contact'),
    'MEMBER_BIRTHDATE' 			=> $this->input->post('birthdate'),
    'MEMBER_DIEDATE' 			=> $this->input->post('diedate'),
    'MEMBER_PID' 			=> $this->input->post('pid'),
    'MEMBER_STATUS' 			=> $this->input->post('status'),
    'MEMBER_COLOR' 			=> $this->input->post('color'),
    'USER_ID' 			=> $this->session->userdata('USER_ID'),
  );
  $result=$this->db->insert('MEMBER',$data);
}
else
{
  $data = array(
    'MEMBER_NAME' 			=> $this->input->post('name'),
    'MEMBER_GENDER' 			=> $this->input->post('gender'),
    'MEMBER_ADDRESS' 			=> $this->input->post('address'),
    'MEMBER_GENDER' 			=> $this->input->post('gender'),
    'MEMBER_CONTACT' 			=> $this->input->post('contact'),
    'MEMBER_BIRTHDATE' 			=> $this->input->post('birthdate'),
    'MEMBER_DIEDATE' 			=> $this->input->post('diedate'),
    'MEMBER_PID' 			=> $this->input->post('pid'),
    'MEMBER_STATUS' 			=> $this->input->post('status'),
    'MEMBER_COLOR' 			=> $this->input->post('color'),
    'USER_ID' 			=> $this->session->userdata('USER_ID'),
  );
  $this->db->where('MEMBER_ID', $this->input->post('member_id'));
  $result=$this->db->update('MEMBER',$data);
}
  return $result;
}
```

## View
```bash

```

## Ajax
```bash
Like Save Data
```
