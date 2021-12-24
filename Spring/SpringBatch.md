### Spring Batch

Spring Batch는 로깅/추적, 트랜잭션 관리, 작업 처리 통계, 작업 재시작, 건너뛰기, 리소스 관리 등 대용량 레코드 처리에 필수적인 기능을 제공합니다. Spring Batch에서 배치가 실패하여 작업 재시작을 하게 된다면 처음부터가 아닌 실패한 지점부터 실행을 하게 됩니다. 또한 중복 실행을 막기 위해 성공한 이력이 있는 Batch는 동일한 파라미터로 실행 시 Exception이 발생합니다.

<br>

### Spring Batch의 용어

* #### Job
    Job은 배치처리 과정을 하나의 단위로 만들어 놓은 객체입니다. 또한 배치처리 과정에 있어 전체 계층 최상단에 위치하고 있습니다.

* #### JobInstance
    JobInstance는 Job의 실행의 단위를 나타냅니다. Job을 실행 시키게 되면 하나의 JobInstance가 생성되게 됩니다. 각 1월 1일, 1월 2일에 Job을 실행시키면 각각의 JobInstance가 생성된다 하지만 1월 1일에 실행된 JobInstance가 실패하면 다시 실행 시키더라도 1월 1일에 실행된 JobInstance에 대한 데이터만 처리하게 된다.

* #### JobParameters
    JobParameters 객체 는 JobInstance를 구별하는 역할을 가집니다. JobParameters는 JobInstance 구별 외에도 개발자 JobInstance에 전달 되는 Parameter(매개변수) 역할도 하고 있습니다. 또한 JobParameters는 String, Double, Long, Date 4가지 형식만을 지원하고 있습니다.

* #### JobExecution 
    JobExecution은 JobInstance의 실행 시도에 대한 객체입니다. 1월 1일에 실행한 JobInstance가 실패하여 재실행을 해도 동일한 JobInstance는 실행 시키지만 이 2번에 실행에 대한 JobExecution은 개별로 생기게 됩니다. JobExecution은 이러한 JobInstance 실행에 대한 상태, 시작시간, 종료시간, 생성시간 등의 정보를 담고 있습니다.

* #### Step
    Step은 Job의 배치처리를 정의하고 순차적인 단계를 캡슐화 합니다. Job은 최소한 1개 이상의 Step을 가져야 하며 Job의 실제 일괄 처리를 제어하는 모든 정보가 들어있습니다.

* #### StepExecution
    StepExcution은 JobExecution과 동일하게 Step 실행 시도에 대한 객체를 나타냅니다. 하지만 Job이 여러개의 Step으로 구성되어 있을 경우 이전 단계의 Step이 실패하게 되면 다음 단계가 실행되지 않음으로 실패 이후 StepExecution은 생성되지 않습니다. StepExecution 또한 JobExecution과 동일하게 실제 시작이 될 때만 생성됩니다. StepExecution에는 JobExecution에 저장되는 정보 외에 Read 횟수, Write 횟수, Commit 횟수, Skip 횟수 등의 정보들도 저장이 됩니다.

* #### ExcutionContext 
    ExcutionContext란 Job에서 데이터를 공유 할 수 있는 데이터 저장소입니다. Spring Batch에서 제공하는 ExecutionContext는 JobExecutionContext, StepExecution 2가지 종류가 있으나 이 두가지는 지정되는 범위가 다릅니다. JobExecutionContext의 경우 Commit 시점에 저장되는 반면 StepExecutionContext는 실행 사이에 저장이 되게 됩니다. ExecutionContext를 통해 Step간 Data 공유가 가능하며 Job 실행 실패시 ExecutionContext를 통한 마지막 실행 값을 재구성 할 수 있습니다.

* #### JobRepository
    JobRepository는 위에서 말한 모든 배치 처리 정보를 담고있는 매커니즘입니다. Job이 실행되게 되면 JobRepository에 JobExecution과 StepExecution을 생성하게 되며 JobRepository에서 Execution 정보들을 저장하고 조회하며 사용하게 됩니다.

* #### JobLauncher
    JobLauncher는 Job과 JobParameters를 사용하여 Job을 실행하는 객체입니다.

* #### ItemReader
    ItemReader는 Step에서 Item을 읽어오는 인터페이스 입니다, ItemReader에 대한 다양한 인터페이스가 존재하며 다양한 방법으로 Item을 읽어 올 수 있습니다.

* #### ItemWriter
    ItemWriter는 처리 된 Data를 Writer 할 때 마다 사용한다. Writer는 처리 결과물에 따라 Insert가 될 수도 Update가 될 수도 있다. Writer또한 Read와 동일하게 다양한 인터페이스 존재한다. Writer는 기본적으로 Item을 Chunk로 묶어 처리하고 있습니다.

* #### ItemProcessor
    ItemProcessor는 Reader에서 읽어온 Item의 데이터를 처리하는 역할을 하고 있다. Processor는 배치를 처리하는데의 필수 요소는 아니며 Readerm Writer, Processor 처리를 분리하여 각각의 역할을 명확하게 구분하고 있습니다.

<br>

### Spring Batch 사용해보기

Spring Batch에서의 Job안에는 Step들이 그룹을 지어 구성되어 있습니다. Job은 순차적으로 Step을 수행하며 Batch를 수행하게 됩니다. Step은 `Tasklet` 처리 방식과 `Chunk` 지향 처리 방식을 지원하고 있습니다.