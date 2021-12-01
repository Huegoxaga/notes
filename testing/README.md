# Testing

## Types of Testing

### Penetration Testing

- It involves simulating attacks against a specific system or network in an attempt to identify certain weak points that could be exploited by black hat hackers
- The terms penetration testing and cyber security testing are often used interchangeably, but penetration testing may be only one part of a cyber security testing plan
- You can’t really write a meaningful cyber security report without having done penetration testing

#### Black Box Testing

- Black box testing refers to tests on systems or software without having (or using) any knowledge of the inner workings of the target
- Generically described as trying various inputs on the system and observing what output/results you receive in order to find patterns, errors, or weaknesses
- Black box testing is a high-level category that many other types of tests fall under
- This is the perspective a black hat hacker always has to start with, and as such black box testing can be useful for examining the system from an outsider's perspective
- The tester must be familiar with scanning tools and must be capable of performing manual penetration tests in an effort to gain more information about the system, including an idea of what the topology looks like

#### White Box Testing

- The opposite of black box testing -- where the tester has and uses knowledge of the inner workings of the system in their efforts to find vulnerabilities
- "The inner workings" might include access to source code, a map of the topology/addresses, knowledge of operating systems and versions in use, the software/services running on each target, etc., etc
- Takes a longer amount of time, as there is a lot of data to go through when exploring for possible attack vectors
- Can be a lot more potent in finding weaknesses, but may not be as realistic compared to black box testing
- Helps to cover the worst-case scenarios as well as attacks from insiders

#### Grey Box Testing

- Appropriately named, grey box testing is where the tester has or uses some but not all knowledge or access on the system (i.e. half way between black box and white box testing)
- It is also from an outsider’s perspective, but assumes that the outsider has managed to gain some knowledge (perhaps they have scanned and mapped the topology) and access (perhaps they have compromised a user account)
- Gaining a “grey box” level of access and knowledge is the initial goal of a black hat hacker
- Grey box testing is more focused and efficient than black box testing, since some information does not need to be determined manually by the tester

#### Load Testing

- Sometimes called a stress test or performance test
- Load testing is a way to measure how a system performs when faced with unusually heavy traffic
- What is considered to be heavy traffic varies from system to system and needs to be defined prior to testing
- The most common load test is a Distributed Denial of Service (DDoS) type of attack

#### Component Testing

- A type of testing in which a system is broken down into its components which can then be individually tested
- Considered a type of white box testing since significant knowledge of the overall system is required in order to determine its components
- A network can be broken down to the individual devices participating in the network, which may all have unique characteristics to test against
- Software today is often written in a modular way -- each module is responsible for a certain functionality of the software. Finding a vulnerability in a single module might expose the entire system

#### Integration Testing

- After looking at the individual parts of the system via component testing, integration testing can be performed
- Integration testing is examining how the individual components interact with each other, which might be the source of vulnerabilities not present when examining the components separately

#### Compliance Testing

- Testing whether the system meets requirements set out by the organization, industry standards, or general best practices
- Might include comparing actual configurations with ones that are deemed to be the most secure for that particular system
- Could involve testing disaster recovery and auditing procedures
- The cyber security industry has not yet been unified under one standard, with some of the more well-known standards being ISO/IEC 27001 and 27002, NIST Cybersecurity Framework, and standards put forward by banking and credit institutions

## Test Case

- Each test should be documented with a test case that includes at least the following information:

  - Test Case Name
  - Unique Identifier
  - Description
  - Test Executed By
  - Test Executed Date
  - Test Start Time
  - Test End Time
  - Test Steps
  - Expected results
  - Actual results
  - Comments
  - Pre- and Post-Conditions

## Test Report

- The report is meant to serve a few purpose
  - Provide information that is actionable from a business perspective, including - Target System – Provide a name for the overall system you are testing. Ex. Customer website, network infrastructure, physical security of the premises, etc. - Client – The organization and person responsible for approval. - Tester - Who are the penetration testers involved? - Provide technical details about discovered vulnerabilities - Possibly act as a remediation guide - Duration - What are the dates that the penetration tests will take place? - If some tests will impact availability, what time will they take place, and for how long? - Software Used - If you are using a penetration testing platform such as Kali Linux, indicate that here, Also include more specific software you are using, such as nmap,
    Metasploit, etc.
    • Test Types
    – Non-specific categories such as network scans, tests for specific
    vulnerabilities, load tests, etc.

## JMeter

- The `Apache JMeter™` application is open source software, a 100% pure Java application designed to load test functional behavior and measure performance
- It has GUI mode which can be used to create the test plan, and a CLI mode or non-GUI mode for running the actual test
  - Test plan file has extension `.jmx`
  - Running test plan in GUI mode should only be used for creation and debugging purpose. To run the real load test, use CLI mode.

### Installation

- On Mac, run `brew install jmeter`
- Modify the `bin/setenv.sh` file for settings like
  - **Increase the Java Heap size**, By default JMeter runs with a heap of 1 GB, this might not be enough depends on the number of threads needed for the test plan

### CLI

- run `/usr/local/Cellar/jmeter/5.4.1/libexec/bin/jmeter.sh` launch JMeter GUI
- `jmeter -n -t test_plan.jmx -l log.jtl -H my.proxy.server -P 8000` run a test plan
  - `-n`, This specifies JMeter is to run in cli mode
  - `-t`, specify the name of JMX file that contains the test plan
  - `-l`, specigy the name of JTL file to log sample results to
  - `-j`, specify the name of JMeter run log file
  - `-H`, proxy server hostname or ip address
  - `-P`, proxy server port

### GUI

- The structure of a test plan can be created on the left panel
- One `Test Plan` can have many `Thread Group`s
  - `Thread Group` is a collection of threads, each thread represents one user
- One `Thread Group` can have many `Sampler`s
  - `Sampler`s are different type of request send by a thread group
- One `Thread Group` can have many `Listener`s
  - `Listener`s are used to store the results
- One `Thread Group` can have many `Config Element`s
  - It can setup defaults and variables for all samplers under that `Thread Group`
- One `Thread Group` or `Sampler` can have a `Timer`
  - `Timer` for `Thread Group` will delay the execution of all samplers belongs to that `Thread Group`
  - `Timer` under a `Sampler` will delay the execution of that sampler
- One `Thread Group` can have one or more `Controller`, each `Controller` can have and controll one or more `Sampler`
  - `Controller` can add logic to the test plan
- Components can be disabled by `Right Click` -> `Disable`

#### Thread Group

- `Ramp-Up Period` - the time JMeter should take to start the total number of threads

#### Sampler

- `HTTP Request`
  - Parameter can be either added to the path or added in the parameter table

#### Listener

- The listener type `View Results Tree` and `View Result in Table` will summary the request performance in tree and table

#### Timer

- `Constant Timer` delay one or more sampler for a specific amount of time
- `Uniform Random Timer` generate a delay time from zero to the `Random Delay Max` time plus the `Constant Delay Offset`

#### Controller

- `Loop Controller`, it is used when samplers under a thread group need to be looped differently

#### Config Element

- `User Defined Variables`, once defined in the table, the variable can be accessed in the sampler setting using `${var_name}`
- `CSV Data Set Config`, each iteration of the sampler will use one record of the variables in the CSV file, from top to bottom repeatly, the values can be accessed from the sampler cofig using `${header_name}`
