# MULTITHREADED PHP

PHP can run multiple thread only with a PHP package called __pthreads__

An example is below

```
class MyThread extends \Thread {

	private $duration = 0;

    public function __construct(int $duration) {
		
		$this->duration = $duration;
	}

	public function run() {
		// Query the database
        $result = mysql_query('SELECT date, value FROM me Where WEEKDAY(date) >="6" AND HOUR(date) >= "0" AND HOUR(date) < "24"');

        $sum = 0;
        while($row = mysql_fetch_assoc($result)) {
            $h1 += $row['value'];
        }
        sleep($this->duration);
        echo $sum;
	}
}

function main() {
	$start_time = time();
	$count = 3;
	$threads = [];

	# Thread Creation
	for($i = 0; $i < $count; $i++) {
		$threads[$i] = new MyThread(rand(1, 3));
	}

	# Thread Running
	for($i = 0; $i < $count; $i++) {
		$threads[$i]->start();
	}

	# Thread joining
	for($i = 0; $i < $count; $i++) {
		$threads[$i]->join();
	}

	# End
	echo "End\n";

	# Execution Time
	echo "--- " . (time() - $start_time) . " seconds ---\n";

}


main();

```

