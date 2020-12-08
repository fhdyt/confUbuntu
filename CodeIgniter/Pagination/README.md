## Controller
```bash
public function index()
{
  $this->load->model('ImageModel');
  $this->load->library('pagination');
  $jumlah_data = $this->ImageModel->count_data();

  $config['base_url'] = base_url().'index.php/home/index/';
  $config['total_rows'] = $jumlah_data;
  $config['per_page'] = 15;

  $config['full_tag_open'] = '<ul class="pagination justify-content-center">';
  $config['full_tag_close'] = '</ul>';

  $config['first_tag_open'] = '<li class="page-item"><span class="page-link">';
  $config['first_link'] = 'First Page';
  $config['first_tag_close'] = '</span></li>';

  $config['last_tag_open'] = '<li class="page-item"><span class="page-link">';
  $config['last_link'] = 'Last Page';
  $config['last_tag_close'] = '</span></li>';

  $config['next_tag_open'] = '<li class="page-item"><span class="page-link">';
  $config['next_link'] = 'Next';
  $config['next_tag_close'] = '</span></li>';

  $config['prev_tag_open'] = '<li class="page-item"><span class="page-link">';
  $config['prev_link'] = 'Prev';
  $config['prev_tag_close'] = '</span></li>';

  $config['cur_tag_open'] = '<li class="page-item active"><span class="page-link">';
  $config['cur_tag_close'] = '</h1>';

  $config['num_tag_open'] = '<li class="page-item"><span class="page-link">';
  $config['num_tag_close'] = '</span></li>';

  $from = $this->uri->segment(3);
  $this->pagination->initialize($config);
  $data['img']=$this->ImageModel->img_list_model($config['per_page'],$from);


  $data['title'] = "Home";
  $this->load->view('template/header',$data);
  $this->load->view('home', $data);
  $this->load->view('template/footer');
}
```

## Model
```bash
public function img_list_model($number,$offset)
{
  $this->db->order_by('IMAGE_DATE', 'DESC');
  $hasil=$this->db->get('IMAGE',$number,$offset);
  return $hasil->result();
}
function count_data()
{
  return $this->db->get('IMAGE')->num_rows();
}
```

## View
```bash

```

## Ajax
```bash

```
