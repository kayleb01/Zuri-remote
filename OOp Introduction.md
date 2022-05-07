#Object Oriented Programming
Object Oriented Programming is a software programming model that relies on the concept of classes and objects. OOP's modular enables programmers to build and manage chunks rather than large amount of code.
In object oriented programming, some of the components in a class are Properties and methods
Properties are attributes of a class, when writing properties in a class you can use access modifiers of access identifier which are public (means the property can be accessed outside the class), private (property can only be accessed within the class it is written) and protected (can only be accessed within the class it is written and a class that extends the class it is written in).
Method are functions in a class.
OOP features:
 - Encapsulation
 - Polymorphism
 - Inheritance
  Example

  ```
  
  Class Student
  {
      /*
      *Properties of the class
      */

      public $student;
      private $student_number;
      protected $level;

      public function __construct($student, $student_number, $level){
          $this->student = $student;
          $this->student_number = $student_number;
          $this->level = $level;
      }

    public function getStudent()
    {
        return json_encode(['name' => $this->student, 'level' => $this->level, 'matric_number' => $this->student_name]);
    }

  }

/** Instantiate the class **/

$student = new Student('foo bar', '2022-03-ac', '200);
echo $sudent;

  ```