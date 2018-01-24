## CodeIgniter
### Framework
프래임워크란 에플리케이션을 구현 할 때 공통되는 부분과 에플리케이션 특화된 부분을 구분해서 공통되는 부분은 미리 만들어진 체계를 이용하고, 에플리케이션 특화된 부분은 직접 구현함으로서 생산성을 향상시키는 수단이다.  
잘 만들어진 프래임워크을 이용하면 높은 퀄리티로 프로젝트를 유지 할 수 있는 장점이 생긴다.
### Controller
[Controller 매뉴얼](http://codeigniter-kr.org/user_guide_2.1.0/general/controllers.html)
### View
 CodeIgniter를 이용해서 화면에 내용을 출력하기 위해서는 Controller에서 echo를 하는 것도 방법이지만, View 안에서 UI와 관련된 코드를 작성하는 것이 바람직하다.
 - `$this->load->view('파일명')`
 - `$this->load->view('파일명',array('id'=>$id))` : 인자전달
### Model
View가 표현을 담당한다면 Model은 데이터를 담당한다. 즉 데이터를 다루는 로직을 모델에 모아둬서 데이터와 뷰를 격리 시키는 것이다. 이를 통해서 코드 관리의 편의성을 높일 수 있고, 향후 데이터베이스를 다른 타입으로 교체가 용이하다.
```
<?php
class Topic_model extends CI_Model{
  function __construct(){
    parent::__construct();
  }
  public function gets(){
    return $this->db->query('select * from topic')->result();
  }
  public function get($topic_id){
    return $this->db->get_where('topic',array('id'=>$topic_id))->row();
    //return $this->db->query('select * from topic where id='.$topic_id)
  }
}
 ?>
```
### MVC 패턴
MVC란 Model View Controller의 약자로 에플리케이션을 세가지의 역할로 구분한 개발 방법론이다. 사용자가 Controller를 조작하면 Controller는 Model을 통해서 데이터를 가져오고 그 정보를 바탕으로 시각적인 표현을 담당하는 View를 제어해서 사용자에게 전달하게 된다.
