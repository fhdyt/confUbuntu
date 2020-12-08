## Controller
```bash
<?php
defined('BASEPATH') OR exit('No direct script access allowed');

class Login extends CI_Controller {

  public function index()
  {
    if(!empty($this->session->userdata('is_login')))
    {
    redirect('profile');
    }
    else{
    $data['title'] = "Login";
    $this->load->view('template/header',$data);
    $this->load->view('login');
    $this->load->view('template/footer');
    }
  }
  public function proses()
  {
    $username = $this->input->post('username');
    $password = $this->input->post('password');
    $this->load->model('LoginModel');
    if($this->LoginModel->login_user($username,$password))
    {
      redirect("profile/upload");
    }
    else
    {
      echo "Gagal";
    }
  }
  public function logout()
  {
    $this->session->unset_userdata('is_login');
    redirect('login');
  }
}
```

## Model
```bash
<?php
class LoginModel extends CI_Model
{

  function login_user($username,$password)
  {
    $query = $this->db->get_where('USER',array('USER_USERNAME'=>$username));
    if($query->num_rows() > 0)
    {
      $data_user = $query->row();
      if (password_verify($password, $data_user->USER_PASSWORD))
      {
        $this->session->set_userdata('USER_USERNAME',$data_user->USER_USERNAME);
        $this->session->set_userdata('USER_ID',$data_user->USER_ID);
        $this->session->set_userdata('is_login',TRUE);
        return TRUE;
      }
      else
      {
        return FALSE;
      }
    }
    else
    {
      return FALSE;
    }
  }
  function cek_login()
  {
    if(empty($this->session->userdata('is_login')))
    {
      redirect('login');
    }
  }

}
?>
```

## View
```bash
<form method="post" action="<?php echo base_url(); ?>index.php/login/proses">
  <div class="form-group">
    <input type="text" class="form-control" name="username" placeholder="Username" autocomplete="off"">
  </div>
  <div class="form-group">
    <input type="password" name="password" class="form-control" placeholder="Password" id="exampleInputPassword1">
  </div>
  <button type="submit" class="btn btn-secondary btn-block">Login</button>
</form>
```

## Ajax
```bash

```
