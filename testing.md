# Testing

## JMeter

* The `Apache JMeter™` application is open source software, a 100% pure Java application designed to load test functional behavior and measure performance
* It has GUI mode which can be used to create the test plan, and a CLI mode or non-GUI mode for running the actual test
  * Test plan file has extension `.jmx`
  * Running test plan in GUI mode should only be used for creation and debugging purpose. To run the real load test, use CLI mode.

### Installation

* On Mac, run `brew install jmeter`
* Modify the `bin/setenv.sh` file for settings like
  * **Increase the Java Heap size**, By default JMeter runs with a heap of 1 GB, this might not be enough depends on the number of threads needed for the test plan

### CLI

* run `/usr/local/Cellar/jmeter/5.4.1/libexec/bin/jmeter.sh` launch JMeter GUI
* `jmeter -n -t test_plan.jmx -l log.jtl -H my.proxy.server -P 8000` run a test plan
  * `-n`, This specifies JMeter is to run in cli mode
  * `-t`, specify the name of JMX file that contains the test plan
  * `-l`, specigy the name of JTL file to log sample results to
  * `-j`, specify the name of JMeter run log file
  * `-H`, proxy server hostname or ip address
  * `-P`, proxy server port

### GUI

* The structure of a test plan can be created on the left panel
* One `Test Plan` can have many `Thread Group`s
  * `Thread Group` is a collection of threads, each thread represents one user
* One `Thread Group` can have many `Sampler`s
  * `Sampler`s are different type of request send by a thread group
* One `Thread Group` can have many `Listener`s
  * `Listener`s are used to store the results
* One `Thread Group` can have many `Config Element`s
  * It can setup defaults and variables for all samplers under that `Thread Group`
* One `Thread Group` or `Sampler` can have a `Timer`
  * `Timer` for `Thread Group` will delay the execution of all samplers belongs to that `Thread Group`
  * `Timer` under a `Sampler` will delay the execution of that sampler
* One `Thread Group` can have one or more `Controller`, each `Controller` can have and controll one or more `Sampler`
  * `Controller` can add logic to the test plan
* Components can be disabled by `Right Click` -&gt; `Disable`

#### Thread Group

* `Ramp-Up Period` - the time JMeter should take to start the total number of threads

#### Sampler

* `HTTP Request`
  * Parameter can be either added to the path or added in the parameter table

#### Listener

* The listener type `View Results Tree` and `View Result in Table` will summary the request performance in tree and table

#### Timer

* `Constant Timer` delay one or more sampler for a specific amount of time
* `Uniform Random Timer` generate a delay time from zero to the `Random Delay Max` time plus the `Constant Delay Offset`

#### Controller

* `Loop Controller`, it is used when samplers under a thread group need to be looped differently

#### Config Element

* `User Defined Variables`, once defined in the table, the variable can be accessed in the sampler setting using `${var_name}`
* `CSV Data Set Config`, each iteration of the sampler will use one record of the variables in the CSV file, from top to bottom repeatly, the values can be accessed from the sampler cofig using `${header_name}`

