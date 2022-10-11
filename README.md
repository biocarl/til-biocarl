# Things to learn and investigate

-   Get updated what is available for vim emulation in IntelliJ, see [Changelog](https://github.com/JetBrains/ideavim/blob/master/CHANGES.md)
-   Privacy engineering, read [link](https://www.ipc.on.ca/wp-content/uploads/resources/7foundationalprinciples.pdf)
-   research value of limiting amount of open tabs
-   Do the [OWASP Juice workshop](https://owasp.org/www-project-juice-shop/)
-   learn about different ways of teaching [link](https://www.youtube.com/watch?v=L0xTXGahEus)
-   Do a proper scrum vs kanban write-up (pros/cons)
-   Read what it means to be a tech lead [here](https://noidea.dog/glue)
-   Learn about thread-safety and extend existing TIL based on this [here](https://www.baeldung.com/java-thread-safety)
-   Next to DRY, there is also the WET and AHA principle (see [here](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself))
-   watch [Patterns of Effective Teams](https://www.youtube.com/watch?v=lvs7VEsQzKY) and Dreyfus model matrix for pairing
-   Learn more about https, [tls handshake](https://www.cloudflare.com/learning/ssl/what-happens-in-a-tls-handshake/) and [Fingerprinting](https://daniel.haxx.se/blog/2022/09/02/curls-tls-fingerprint/)
-   read about cycles of group development in software teams, [paper](https://www.researchgate.net/publication/247720440_Software_Team_Formation_and_Decay_Extending_the_Standard_Model_for_Small_Groups)
-   Introduce syntax
    -   manually label (hierachical)
        -   whenever you define a new label you need to specify the parent label
            -   `tag1<tag2`
        -   you can tag entire entries or single bullet points
    -   in the end you would have a single graph of hierachical labels and forest with entities (childs are backlinks)
-   other ideas
    -   generate edit links so you do not have to scroll down when editing old entries?
    -   how to integrate Anki into this (batch-upload from time to time)
-   🎧: [brown noise](https://www.youtube.com/watch?v=RqzGzwTY-6w) and [rainymood](https://rainymood.com/)

---

# 📅 28.09.2022 python: Spin-Up local server for serving files

-   useful if you want to link local files in a Google Doc document
-   currently Google Doc only allows http/https protocol and not brower based local file like `file:///`

``` {.bash}
cd path/to/files
python3 -m http.server 8000
```

-   this results in localhost links like `http://0.0.0.0:8000/some.pdf`
-   for pdf\'s you can also link to a specific page like `http://0.0.0.0:8000/some.pdf#page=5`

# 📅 24.09.2022 Fun: If the client does not pay for a website

-   [link to repo](https://github.com/kleampa/not-paid)

# 📅 23.09.2022 Workshop: Game-Retrospective

-   Create a game board with fields (with special actions)
-   Members get a dice and move along the board one by one
-   the winner facilitates the next retro
-   Possible actions
    -   Give one college positive feedback
    -   Say something which went Good/Bad in this iteration
    -   Name a topic and everyone in their round has to give his opinion to this topic
    -   Give a suggestion what to improve next iteration. If the majority likes the idea you are allowed to throw a dice again
    -   Propose a topic/challenge and facilitate a small discussion for the next n minutes

# 📅 22.09.2022 intellij: Pass to pass VM options to run configuration

-   `Edit Configuration` \> `Modify Options` \> `Add VM Options`
-   Example entry for setting a system property: `-Dfail_on_exception=true`

# 📅 21.09.2022 junit: Run test classes from one accumulating classes, sharing common annotations

-   Use this approach only if you want to share annotations in one class
-   `@BeforeEach`, `@AfterEach`, `@ExtendWith` are all also applied to the nested ones

``` {.java}
@SomeAnnotation //it depends on the implementation of the annotation if that annotation will be passed down to the nested classes, otherwise you can also annotate the nested class
public class SuperTest {

    @Nested // class will be executed as TestClass
    public class ChildATestRun extends ChildATest {}

    @Nested
    @DisplayName("If you split by scenario you can put the scenario here")
    public class ChildBTestRun extends ChildBTest {}
}

// Single Test classes are abstract so that they are not run twice by junit
public abstract ChildATest {}
```

# 📅 21.09.2022 Gradle: Pass system property to gradle task

-   Retrieve system property from calling side and pass it to executing jvm: `systemProperty "myvariable", System.getProperty("myvariable")`

# 📅 19.09.2022 Java: `@Inherited` annotation

-   Meta annotation which tells compiler that annotated annotation will be inherited to child classes
-   this is only valid for classes, on methods it is ignored.

# 📅 12.09.2022 Gradle: Define custom gradle source sets

-   `src/main/java` and `src/test/java` are assumed default source directories
-   to create custom source sets:

``` {.groovy}
// define custom source set
sourceSets{
    minion {
        java {
            srcDirs("src/minion")
        }
    }
}

// define dependencies only used for that source set
dependencies {
    minionImplementation('com.google.guava:guava:29.0-jre')
}

// if you want to run tetss on specific source set
task runMinionTest(type: Test) {
    description = "Run integration tests"
    group = "verification" // task will associated with that folder
    useJUnitPlatform() // Discover and execute JUnit Platform-based tests
    testClassesDirs = sourceSets.minion.output.classesDirs
    classpath = sourceSets.minion.runtimeClasspath
}

// if you want to inherit dependency declarations from different
configurations {
    minionImplementation.extendsFrom(testImplementation)
}

// if you need the compiled classes from one sourcset (here main) in another source set
sourceSets{
    minion {
        compileClasspath += sourceSets.main.output
        runtimeClasspath += sourceSets.main.output
    }
}

```

-   For more information on configuring test task see here [here](https://docs.gradle.org/current/javadoc/org/gradle/api/tasks/testing/Test.html)

# 📅 10.09.2022 mac: Repeat keys on long-press

-   `defaults write -g ApplePressAndHoldEnabled -bool false`

# 📅 10.09.2022 mac: Custom keyboard layout with Ukulele

-   `New from current Input source ...` to load current keyboard map
-   Edit with right click, `Edit key` and specifiy output and modifier
-   Move file into `/Library/Keyboard Layouts/`, restart and select layout under keyboard preferences
-   IntelliJ: If you want to use the option modifier key you need to select `Keymap` -\> `IntelliJ Idea Classic` (and not mac)

# 📅 08.09.2022 github: Exclude filenames from search

-   for instance if you want to exlude the actual implementation source (which many people fork) and want to see how that piece of code is used
-   `-filename:composer.json`

# 📅 08.09.2022 cs: Shannon Entropy

-   [source](https://www.quantamagazine.org/how-claude-shannons-concept-of-entropy-quantifies-information-20220906/)
-   if you want to store/communicate for instance a series of random coin flips you need a lot of information because the series does not follow a inherit structure: What is the amount of information needed to accurately transmit the message?
-   general rule: the more information you can predict about the message the more information you need
    -   2x coin-flip with coin of two heads -\> zero information needed
    -   2x coin-clip with normal coin -\> 2 bits of information needed (just guessing is 25% probability you get it right)
-   that threshold of the minimum bits needed to resolve ambiguity entirely is called Shannon Entropy, below that threshold the likelihood increased that message will be corrupted
-   Shannon Entropy can be framed as number of yes-no questions needed to resolve the contents of a message (think of Akinator, see also [Twenty Questions algorithm](https://en.wikipedia.org/wiki/Twenty_questions))
    -   the more uncertainty about e.g. weather for the next days is the more questions you need to ask to get all right (e.g. is every day sunny vs is mon,tue,.. sunny?)
    -   for english words you need less questions about the characters because language follows certain probabilities (e.g. frequency of vowels), but for an entirely random string you need to cycle through all characters for each character you want to guess. Implication: Humans comunicate a lot with relatively little information (better with chinese)
-   also used to detect secrets in code (see secret detection), but also information compression
-   for example when compressing a video pixels and how they change to the next frame also allow for pattern prediction (similar to language patterns)

# 📅 08.09.2022 Team: Tech Health Check The following questions can be answered or voted on with 3 degrees on satisfaction

-   How is the experience of building your service?
-   How is the experience of testing your service?
-   How is the experience of deploying your service?
-   How is the experience of operating your service?
-   Health of Codebase?

# 📅 08.09.2022 Java: Using testcontainer

-   call docker container from Java
-   You can either use a ready-made dependency which wraps test container logic around the container or do it yourself to not having to use a generic container (e.g. not good if you want to bind certain methods to a custom type when e.g. mocking this out as a dependency)
-   can also be bound to test lifecycle e.g. `@Container` restarts the container for each test
-   How to introduce a custom testcontainer type which receives commands

``` {.java}
import org.testcontainers.containers.GenericContainer;
import org.testcontainers.containers.wait.strategy.Wait;
import org.testcontainers.utility.MountableFile;

public class MyCustomContainer extends GenericContainer<MyCustomContainer> {
    private MyCustomContainer() {
        // docker image (complete url required!)
        super("registry.hub.docker.com/IMAGE:latest");
        // inject envs
        withEnv(Map.of("ENV1", "val1"));
        // hack for keep running the container
        withCommand("tail -F anything");
        // timing when the container is ready for receiving commands
        waitingFor(Wait.forLogMessage(".*tail.*", 1));
        // avoid having the container restart (if you also set testcontainers.reuse.enable=true)
        withReuse(true);
    }

    private int executeCommands(String... command) throws IOException, InterruptedException {
        final ExecResult execResult = super.execInContainer(command);
        System.err.format("Stdout of %s = %s", Arrays.toString(command), execResult.getStdout());
        System.err.format("Stderr of %s = %s", Arrays.toString(command), execResult.getStderr());
        return execResult.getExitCode();
    }

    // Some example how to copy files into container
    public void copyFiles() throws IOException, InterruptedException {
        copyFileToContainer(MountableFile.forHostPath(new File("someFile.txt").getParent()), "somePathInContainer");
        setWorkingDirectory("/tmp");
    }
}
```

# 📅 08.09.2022 Java: Parsing cli args with commons-cli

-   allows for several identical flags `./tool --flag1 arg1 --flag2 args2`
-   allows for required params
-   allows for help output

``` {.java}
import org.apache.commons.cli.*;

Options options = new Options();
options.addOption(Option.builder("FLAG1")
    .required()
    .longOpt("flag1")
    .desc("Some description")
    .hasArg() // is not a boolean value
    .build());

CommandLineParser parser = new DefaultParser();
CommandLine cmd;
try {
    cmd = parser.parse(options, args);
    // retrieve argument/boolean of first passed flag1
    cmd.getOptionValue("FLAG1");
    // retrieve args of all flags e.g. --flag2 arg1 --flag2 arg2
    cmd.getOptionValues("FLAG2");
} catch (ParseException e) {
    e.printStackTrace();
    System.exit(1);
}
```

# 📅 07.09.2022 InfoSec: Secret dectection

-   many of the reported incidents are usually due to checking in hard-coded secrets into code
-   How does it work? Tools commonly look for
    -   typical filenames and format conventions like `secret.json` or `Bearer XZS`
    -   looking for high entropy strings
        -   how is is it to describe the characters in less characters, hard to predict character distribution
        -   Example `aaaaaaabbbbbbbcccccc` vs `doasolkasnvpa`
        -   see more in [Entropy (information theory)](https://en.wikipedia.org/wiki/Entropy_(information_theory))
-   Two ways of doing secret detection
    -   Preventive: Prevent from uploading secret
        -   detect secrets as part of a git hook
        -   for git hook there is frameworks like [pre-commit](https://pre-commit.com/) which allow you managing different git hooks (for instance running linter check before commit)
    -   Detection
        -   check also in the pipeline (scan repo for secret)
        -   also services which do OSINT to check if a secret for yours was exposed like [keynuker](https://github.com/tleyden/keynuker) which automatically destroys found aws keys
-   tools for secret detection
    -   [talisman](https://github.com/thoughtworks/talisman)
    -   [whispers](https://github.com/Skyscanner/whispers)
    -   [trufflehog](https://github.com/trufflesecurity/trufflehog)
    -   [trivy](https://github.com/aquasecurity/trivy)

# 📅 07.09.2022 Java: Handle blank strings in System.out.format with conditional prefix (hacky/bad idea)

-   **!!** This also works with strings you want to print out, because i̱s interpreted only then
-   Use this when you need to construct a string with optional fields which also influence previous characters

``` {.java}
import org.apache.commons.lang3.StringUtils;
// will end up deleting + when timezone is blank 
System.out.format("12:12:22+%s", StringUtils.defaultIfBlank(timezone, "\b"));

// or use nullable for null params
import static java.util.Optional.ofNullable;
System.out.format("12:12:22+%s", ofNullable(timezone).orElse("\b"));
```

# 📅 03.09.2022 InfoSec: Security by obscurity

-   Concept of breaking standards to make it more difficult for an malicious user/hacker/bot to enter a system
-   Examples
    -   Use different port for ssh
    -   Change admin login url of CMS
    -   Next to user agent also check for tls handshake e.g. you can fingerprint curl with this - see [here](https://daniel.haxx.se/blog/2022/09/02/curls-tls-fingerprint/)
-   This strategy is usually only good for keeping unsophisticated bots out. But even they can [fusk](https://en.m.wikipedia.org/wiki/Fusker), crawl, brute force a lot of those mitigations

# 📅 02.09.2022 Testing: Testing beforehand vs Improved observability

-   Sometimes things are very hard to test
-   If the potential failure scenarios are not too severe you can also opt for putting metrics in place alerting if something is off
-   For example infrastructure code you often do not unit test but try to alert when certain configuration is wrong (service not available, open ports etc.)

# 📅 02.09.2022 Ruby: Monkey patching

-   Monkey patching := Dynamically modify classes/modules/attributes at runtime, allowing for instance to replace methods with side effects in a test
-   Usually only scripting languages allow this (like Ruby/Python)
-   Often used for patching a bug from a third party lib

# 📅 01.09.2022 Docker: Override entrypoint with interactive shell on container start

-   `docker run -it --entrypoint /bin/bash IMAGE`

# 📅 01.09.2022 Git: Switch to previous branch

-   `git switch -`

# 📅 31.08.2022 Docker: Use alpine image with bash

-   Add this to `Dockerfile`: `RUN apk update && apk add bash`

# 📅 31.08.2022 Gradle: Zip/Tar

-   you can use [tarTree](https://docs.gradle.org/current/dsl/org.gradle.api.Project.html#org.gradle.api.Project:tarTree(java.lang.Object)) and [zipTree](https://docs.gradle.org/current/javadoc/org/gradle/api/Project.html#zipTree-java.lang.Object)

# 📅 31.08.2022 Gradle: Exposed standard paths

-   `$buildDir`: where the build folder is generated
-   `src/config.xml`: relative path only from where `build.gradle` is located

# 📅 29.08.2022 Fun: Random fun commit messages

-   [whatthecommit](http://whatthecommit.com/)

# 📅 29.08.2022 Git: Clone from branch directly

-   `git clone --branch <branch> <url>`

# 📅 27.08.2022 Fun: Sleep sort

-   find a numerical representation of each entry and spawn a separate thread for each entry only printing the result after the specified time
-   [source](https://rosettacode.org/wiki/Sorting_algorithms/Sleep_sort)

# 📅 27.08.2022 InfoSec: Web beacon

-   Web beacon:= describes several techniques to determine if someone has visited a website, read a Email or accessed certain content
-   Most simple approach: Embedded Image in email and verify in asset server logs if asset was accessed
    -   this is as initially even a non-visible picture, containing a single pixel (\"tracking pixel\")
-   Be careful which Email you forward because this can be detected by the mechanism described above
-   Minimal information which always can be acquired
    -   IP
    -   Access time
    -   client/browser agent
-   Phishing/Spammer groups also use this to check if certain email are still actively used and if a Mail goes through a spam filter
-   To circumvent such trackers
    -   configure client to not download Assets in emails
    -   Use mail filters (see milter) and configure mail transfer agents (MTA)

# 📅 19.08.2022 java: Thread-Safety and how to achieve it

-   Java has this out of the box, running several worker threads in JVM
-   thread-safety := Different thread can access the same ressource without conflict like simultaneous updates etc.
-   Different approaches to ensure thread-safety
    -   Avoid shared state for instance in a method scoped calculation
    -   Immutable objects (state can\'t be changed after construction and therefore not shared)
    -   🚧 Add others, see TODO\'s

# 📅 18.08.2022 mac: How keys map to windows keys

-   Command (or Cmd) `⌘` : Windows logo key
-   Option `⌥` : Same as `Alt`
-   Control `⌃`: Same as `Ctrl`
-   Shift `⇧`: analogous
-   Caps Lock `⇪`: analogous
-   `Fn`: analogous

# 📅 18.08.2022 mac: Paste without formatting

-   `⌘` + `⌥` + `⇧` + `V` : Paste without formatting

# 📅 14.08.2022 android: How to make file transfer work

-   if device is not found, go to `Developer options` -\> `Default USB configuration` (not found via search!) -\> `File Transfer`

# 📅 14.08.2022 InfoSec: Smartphone as a single point of failure

-   [source](https://news.ycombinator.com/item?id=32396685)
-   Nowdays everything goes over 2FA, if you loos your phone or is stolen you potentially lock out yourself out of a lot of services, requiring a lot of effort to recover all accounts
-   Instead of using Google Authenticator for generating Soft token TOTP\'s you can use solutions like [authy](https://authy.com/)
    -   supports multiple devices at once
    -   you can also use your laptop as device
    -   has encrypted backups (cloud option)
-   Time-based One-time Password (TOTP) := Standardized algorithm using a shared secret approach. Both sides share a time-synced secret which have to match
    -   usually valid for 60 seconds
-   One-time password (OTP) := Server sends out one-time password via E-Mail/SMS.
-   More about pros/cons of TOTP/OTP can be read [here](https://www.transmitsecurity.com/blog/totp-the-good-the-bad-and-the-ugly)

# 📅 12.08.2022 intellij: Why are annotations like `@Override` evaluated while editing?

-   IntelliJ is generating a (unified) abstract syntax tree (AST/UAST) called Program Structure Interface (PSI) while you type
-   Syntax errors are generated by iterating over the PSI tree and check with some language specific grammars for errors, see [here](https://plugins.jetbrains.com/docs/intellij/syntax-errors.html)
-   in the case of the `Override` annotation a custom logic in IntelliJ is implemented to verify if this method actually fufills all the requirements e.g. if the method exists in the parent class [checkOverrideEquivalentInheritedMethods](https://github.com/JetBrains/intellij-community/blob/9306a30b5cda48535edc70af1a2a1a37ac6ef3df/java/java-analysis-impl/src/com/intellij/codeInsight/daemon/impl/analysis/HighlightMethodUtil.java#L1548) but also `checkStaticMethodOverride`, `checkMethodIncompatibleThrows`, `checkSuperMethodIsFinal`
-   it is important to note that it is not continously compiling but just update the AST, in contrast for example to Eclipse which does something like continous compilation which achieves the same
-   With the PSI tree you can do a lot of things out of the box when you want to write your own plugins e.g. finding overwritten methods [here](https://plugins.jetbrains.com/docs/intellij/psi-cookbook.html) for a super method
-   Lombok for instance is using a lot of annotation post processing capabilities, instead of generating code based on code only at compile time you can utilize a plugin for IntelliJ which integrates with the PSI and dynamically generate required sources based on the annotations you provide (not needing to wait for compiling source first)

# 📅 11.08.2022 psychology: Visualizations of common work psychology

-   Credits go to [@alexmaesej](https://www.instagram.com/alexmaesej)
-   Growth mindset and working on a annoying problem:

```{=html}
<p align="center"><img height=400 src="https://raw.githubusercontent.com/biocarl/img/master/psychology/attitude.png" /></p>
```
-   Pairing and wanting to resolve a problem before finishing the day:

```{=html}
<p align="center"><img height=400 src="https://raw.githubusercontent.com/biocarl/img/master/psychology/focus.png" /></p>
```
-   Working with a new technology:

```{=html}
<p align="center"><img height=400 src="https://raw.githubusercontent.com/biocarl/img/master/psychology/starting_a_task.png" /></p>
```
-   Doing TIL\'s:

```{=html}
<p align="center"><img height=400 src="https://raw.githubusercontent.com/biocarl/img/master/psychology/consistency.png" /></p>
```
-   Reflecting about growth and technical journey in general:

```{=html}
<p align="center"><img height=400 src="https://raw.githubusercontent.com/biocarl/img/master/psychology/not_giving_up.png" /></p>
```
-   Doing TIL\'s:

```{=html}
<p align="center"><img height=400 src="https://raw.githubusercontent.com/biocarl/img/master/psychology/discipline.png" /></p>
```
-   Splitting sub tasks of story to not get overwhelmed:

```{=html}
<p align="center"><img height=400 src="https://raw.githubusercontent.com/biocarl/img/master/psychology/one_step_at_a_time.png" /></p>
```
# 📅 10.08.2022 Fun: Where does the name git come from?

-   Torvalds the creator of `git` stated: \"I\'m an egotistical bastard, and I name all my projects after myself. First \'Linux\', now \'git\'.\"
-   `git` means unpleasant person in British English slang
-   man pages describes Git as \"the stupid content tracker\"

# 📅 10.08.2022 Fun: Where does the term logging come from?

-   comes from \"logbook\", which originates from how pirates used to measure the speed of their boat and then write their values into their logbook
-   how did they measure the speed?
    -   1.  Throw log over boat attached to a rope with knots as distance markers

    -   1.  Now count the knots over time and therefore termine the speed

    -   1.  Write it into your logbook

# 📅 09.08.2022 Maven: How to pass in environment variables or system properties in cli

``` {.bash}
# for system property
mvn test -DSYSTEM_PROPERTY="PROPERTY_VALUE" 
# for env var
ENV="VALUE mvn test
```

# 📅 05.08.2022 Java: How to pass in environment variables as annotation parameter?

-   in short, you can\'t generate values dynamically to pass into a annotation because the annotations are evaluated at compile time (baked into the `.class` file)
-   but you can defer evaluation to runtime, this really depends on the implementation of the annotation
-   for instance when you want to pass in an environment variable there is (e.g. for spring) the following convention

``` {.Java}
@Annotation(param="${ENV_VAR:DEFAUlT_VALUE}")
public class SomeClass(){}
```

-   a value resolver is then running during runtime, calling (in this case) `System.getenv(String)`

# 📅 05.08.2022 Fun: Online games to play within the team

-   [garticphone](https://garticphone.com/)
-   [codenames](https://codenames.game/)

# 📅 03.08.2022 consulting: Pyramid principle

-   helps to prioritize contents when you having limited time
-   Steps
    -   \(1\) put core message first and declare it as such
    -   \(2\) what is arguments supporting the core message?
    -   \(3\) what information/details support those arguments?
-   usually the other way round - conclusive approach: facts first - conclusion last
-   when to use:
    -   good for factual topics (very good for management discussions)
-   when not to use:
    -   not very good for educational or emotional topics
    -   you ommit explanations
    -   does not convey emotional value, just objective facts
    -   example: marriage proposal
        -   do not start with we should marry and then give some facts for it
        -   better to do some build up, and get emotional stories around it
-   techniques
    -   clear core message, no vague intentions: what do you really want to achieve?
    -   leave out details which do not support core message
    -   story of the slides should be understandable just by the titles
    -   every slide has only one topic, if not split

# 📅 03.08.2022 vim: Better word navigation with `e`

-   instead of `w` also consider using `e` which jumps to the end of each word
-   if you want to cut the end of a word instead of `dt<whitespace>` use `de` (delete beginning of word `db`)

# 📅 03.08.2022 vim: Replacement mode

-   `R`: Enters replace mode (leave with `ESC`)

# 📅 02.08.2022 microservice: Types of monoliths

-   Single Process Monolith := Code is deployed in a single process. In some sense distributed because it talks e.g. with a database.
-   Modular Monolith := Consists of modules where it can be independently worked on but still requires one overall deployment.
-   Distributed Monolith := Different service but need to be deployed together. Usually occurs when the information hiding principle was not applied.

# 📅 02.08.2022 microservice: Advantage of monoliths

-   Often simpler developer workflows, monitoring and trouble shooting
-   Often e2e testing is simpler
-   Code reuse is easier
-   Fast changing domain

# 📅 01.08.2022 queues: Why to use Avro vs JSON for the event format?

-   (+) optional specification for the event including versioning (public documentation)
-   (+) more space-efficient (e.g. uses pointers to field descriptors, therefore not repeated)
-   (+) direct mapping to json format
-   (-) binary format
-   other option to Avro is Protobuf

# 📅 01.08.2022 InfoSec: Types of Application Security Testing (AST)

-   [source](https://www.hackedu.com/blog/sast-vs-dast-vs-iast)
-   The general idea of shifting security left
    -   shifting security left: lot of parallels to the left shift concept of testing
        -   e.g. in the traditional testing approach you had the QA wall of confusion at the very end of delivery, and in InfoSec you have like two weeks before going life some onboarding of some internal InfoSec specialist or doing some external pen testing -- both approaches produce a lot of overhead because information is lost in the way and quality or security is not baked in
    -   bake in security in our QA process, not even before it, we want to think of security during refinement, or run a *security objectives workshop* right at the inception phase
    -   Secure coding practices and code reviews are **not** enough need for automation --\> new emerging field of DevSecOps
    -   Read more of shifting security to left and different tools helping with that [here](https://www.aquasec.com/cloud-native-academy/devsecops/shift-left-devops/)
-   Static Application Security Testing (SAST)
    -   Whitebox approach, looking at the code
    -   Like a code review but a lot faster
    -   Rules are modifiable and can include
        -   input validation errors, path traversals, injections, race conditions
    -   Detects early in the software dev lifecycle
    -   Pinpoints to the exact location of the code
    -   Can't detect logical vulnerabilities e.g. access control issues
    -   Especially large codebase: false positives (needs expertise to decide on reports)
-   Dynamic Application Security Testing (DAST)
    -   Blackbox approach
    -   Like automated pen testing
    -   Checks things a SAST might miss out on
        -   Checking against running web application, also target infrastructure (webserver, databases, proxies)
        -   including logical vulnerabilities
        -   technology independent
    -   Usually follows the three phases of pentesting (Explore, Exploit, Report)
    -   Drawbacks
        -   Can't identify logical issues
        -   Can't pinpoint spot in code (blackbox approach)
        -   Might corrupt test data
-   Interactive Application Security Testing (IAST)
    -   Combination of SAST and DAST
    -   Best of two worlds: Example
        -   Candidate for SQL injection
        -   Payload is sent
        -   Monitoring confirms if this worked out
    -   And checking for publicly available vulnerabilities
    -   Active IAST, monitoring + attack scenarios
    -   Passive IAST, only monitoring
    -   Fewer false positives
    -   Drawback: Very tedious to setup since it tightly integrates with the application/infrastructure (e.g. setting up the security sensors)
-   Runtime Application Self-Protection (RASP)
    -   Like a guardian angel
    -   sense an attack happening (diagnostic mode) and implement necessary measures (protection mode)
        -   Can block individual requests (like WAF)
        -   Virtually patch a vulnerability to prevent further attack
    -   monitor the inputs, outputs, and internal state
    -   Does not do extensive scans but monitors passively in prod (IAST only during testing phase)
    -   zero-day protection
-   read more about pros/cons of SAST/DAST tools [here](https://owasp.org/wwwcommunity/Free_for_Open_Source_Application_Security_Tools)
-   read more about different criteria when it comes to choosing a AST tool [here](http://projects.webappsec.org/w/page/66094278/Static%20Analysis%20Technologies%20Evaluation%20Criteria)
-   Some options
    -   SAST
        -   Free: Semgrep
        -   Paid: SonarQube
    -   DAST
        -   Free: OWASP ZAP
        -   Paid: Burp Suite
    -   IAST
        -   Contrast Assess

# 📅 01.08.2022 InfoSec: Pentesting 101

-   Usually split up in three phases
-   1.) Explore e.g. Crawl pages, find different entry points, OSINT, software/patches installed, hidden contents
-   2.) Attack -- exploit vulnerabilities in order to prove that they exist
    -   Check for common vulnerabilities
        -   SQL Injections
        -   XSS
        -   LFI
        -   SSRF
    -   Check for authentication issues, memory leaks, session issues, and weak ciphers
-   3.) Report
    -   Result including
        -   URL
        -   attack vector
        -   Complexity of exploit
        -   vulnerability type
        -   Severity

# 📅 29.7.2022 Clojure: Learnings about instaparse

-   a parse library where you just need to define a context-free grammar
-   when you want to match a certain rule, but hide it in the output you can wrap `<>` around

``` {.Clojure}
;; - a matching rule:
'<(>' A* '<)>' ;; -> parens won't be part of group
;; - around a definition:
<BulletMarker> = <'+' | '*' | '-'> ;; -> won't be part of the syntax tree, just helper for the grammar (refered as Hiding tags)
```

-   Do comments with `(* Unordered lists *)`

# 📅 29.07.2022 hikari: Connection pool datasource

-   Important parameters
    -   `maximum-pool-size`: Defines number of allowed connection to datasource, connections will be reused
        -   `minimum-idle`: Defines the number of connections which will be established right away, even though they are not needed (defaults to `maximum-pool-size`)
-   [see documentation](https://github.com/brettwooldridge/HikariCP)

# 📅 29.07.2022 IntelliJ: Refactor current selection/scope

-   `CRTL` + `ALT` + `SHIFT` + `T`: `Refactor this ...`

# 📅 29.07.2022 Workshop: Find out reasons for a check-in over several dimensions

-   **1. Step:** Voting on several dimensions with a gradient (e.g. Fun `(--1--, --2--, --3--)`)
-   **2. Step:** You could span a two-dimensional field where you allow votees to also arrange reasons for their voting on that voting matrix: Fun `(--1-(sticky1)-, --2--, --3-(sticky2)-)`
-   **3. Step:** Votees can vote again on the dimension for further discussion

# 📅 29.07.2022 Fun: Agile Rhapsody

-   One of the more famous agiles songs - [link](https://www.youtube.com/watch?v=MCwJfETgiVo)

# 📅 29.07.2022 InfoSec: CIS benchmarks

-   Center for Internet Security (CIS) := Non-Profit to establish global guidelines for good security standards.
-   CIS benchmarks := benchmark can be used to help an organization build a set of security policies and processes to protect data and assets for a certain technology.
    -   benchmarks available for cloud platforms (like gcp, aws, azure etc.)
-   Tools which are also checking for CIS benchmarks: gcp security control center, snyk, prisma cloud

# 📅 22.07.2022 InfoSec: Injection vulnerabilities

-   Local File Inclusion (LFI) := Web application loads up files on the file system that should not be available
    -   Change `http://example.com/file.php?file=main_page.php` to `http://example.com/file.php?file=../../../etc/passwd`
-   Remote File Inclusion (RFI) := Web application loads up remote files which should not be available
-   Server-side request forgery (SSRF) := Make web application a request which is under the hackers control
    -   Example: Accessing Cloud metadata e.g. `hxxp://metadata.google.internal/computeMetadata/v1/project/project-id` of the running VM
-   SSRF vs LFI/RFI
    -   LFI/RFI is usually a consequence of a SSRF
    -   SSRF is the more general concept and is not bound to a specific file
-   Cross Site Script Inclusion (XSS) := Malicious script in the generated html, whereas backend is only vector but client in frontend is target

# 📅 21.07.2022 Clojure: Print to stderr

``` {.Clojure}
(.println *err* (str "uha!"))
```

# 📅 21.07.2022 Git: Show last stashes

-   `git stash list`: Show last stashes

# 📅 21.07.2022 Team: PowerPoint Karaoke

-   candidate has to present a deck of slides about a topic he never has seen before
-   there is a whole [community](https://de.wikipedia.org/wiki/Powerpoint-Karaoke) around it with tournaments etc.

# 📅 21.07.2022 InfoSec: PII vs PHI

-   Personally Identifiable Information (PII) := Information that can be used to deferr someones identity.
    -   Leakage of PII can lead to \"issues like personal embarrassment, workplace discrimination, and identity theft\"
-   Protected Health Information (PHI) := Health related information that has individual identifiers (PII) associated to it.
    -   \"violation of these can lead to severe legal consequences\"
    -   can lead to embarrassment, financial harm, potential discrimination based on health-issues

# 📅 20.07.2022 Unix: Using grep recursively and for specific file type

-   `grep -r --include "*.txt" <patterm> .`: Search through folders recursively including extension filter

# 📅 20.07.2022 Java: Source-level annotation Processing

-   Annotation Processing := process of generating code at compile time to handle the annotations
-   Allows you to generate additional source files at compilation stage
-   compiler searches for annotations, and matches a annotation processor
-   the annotation processors will then generate source files
-   those source files are scanned again for annotations, cycle is repeated till no new files are generated
-   tutorial how to build custom processing is [here](https://www.baeldung.com/java-annotation-processing-builder)

# 📅 20.07.2022 Java: Do semantic comparision/assertion on two different DTOs with assertj

``` {.Java}
import static org.assertj.core.api.Assertions.assertThat;

assertThat(actual).usingRecursiveComparison()
                .ignoringFields("fieldA", "fieldB", // fields only present in actual or different values
                                "fieldC", "fieldC"  // fields only present in expected or different values
                ) .isEqualTo(expected);
```

# 📅 20.07.2022 Java: MapStruct Basics

-   Learnings and comments (source: [here](https://www.baeldung.com/mapstruct))
    -   generates mapper classes at compile time (see `build/generated/sources/annotationProcessor`)
        -   that\'s why it is [super fast compared to other solutions](https://www.baeldung.com/java-performance-mapping-frameworks#1averagetime)
    -   in-depth documentation [here](https://mapstruct.org/documentation/stable/reference/html/)
    -   out-of-the-box implicit type conversions (e.g. String -\> Date), therefore it is better to explicitly define a mapping method and use a `qualifiedByName` (see below)
    -   when fields are identical (name and hierachy) they are automatically mapped (no `@Mapping` needed)
    -   `@BeforeMapping~/~@AfterMapping` allows to post/pre-process the mapped object, useful e.g. if you want to do some invariant checks (see more [here](https://mapstruct.org/documentation/dev/api/org/mapstruct/AfterMapping.html))
    -   You can provide a default value if to be mapped value is null `@Mapping(defaultExpression ="java(java.util.UUID.randomUUID().toString())")`
-   Define Mapper

``` {.Java}
import org.mapstruct.Mapper;

@Mapper
public interface TargetClassMapper {
    // [1] field in source needs to reference method parameter sourceClass
    @Mapping(source = "sourceClass.fieldA", target = "fieldA")
    TargetClass toTargetClass(SourceClass sourceClass);

    // [2] if type is different provide a conversion method
    default TargetTypeForFieldA convertTypes(final SourceType fieldA) {
        //...
    }

    // [3] if signature is not enough for selecting the right method you can add qualifiers
    // e.g. if you define a String -> String method without qualifier it will overwrite all mappings which contain a String to String mapping
     @Mapping(source = "sourceClass.fieldA", target = "fieldA", qualifiedByName="checkQualifiedNamed")

     @Named("checkQualifiedNamed")
     default TargetTypeForFieldA convertTypes(final SourceType fieldA) {
        //...
    }
}
```

-   all other fields with same name/hierachy will be automatically mapped

```{=html}
<!-- -->
```
-   Use Mapper for example in Spring as Bean

``` {.Java}
import org.mapstruct.factory.Mappers;

@Configuration
public class MapstructConfig {
    @Bean
    public TargetClassMapper targetClassMapper(){
        return Mappers.getMapper(TargetClassMapper.class);
    }
}

// instead of a bean config you can also add the mapper like this
@Mapper(componentModel = "spring")
public interface TargetClassMapper {}
```

-   if you want to see debug output in gradle

``` {.Gradle}
tasks.withType(JavaCompile) {
    options.compilerArgs = [
            '-Amapstruct.verbose=true'
    ]
}
```

-   if you want to fail when target (or source) has unmapped field

``` {.Java}
@Mapper(unmappedTargetPolicy = ReportingPolicy.ERROR)
```

# 📅 20.07.2022 Java: Annotation Theory

-   Annotations can be either interpreted at compile time or at runtime
-   How are annotations e.g. `@Test` related to introspection/reflection? ([source](https://stackoverflow.com/a/1918154))
    -   annotations are `meta-meta objects` describing `meta-objects` (like classes or methods) which themselves describe `objects` (like a instance)
    -   the process of retrieving the metadata of an object at runtime is called *introspection* (see introspection) `anObj.getClass()`
    -   after retrieving the `meta-object` you can also retrieve the annotations `aClass.getAnnotations`

# 📅 20.07.2022 Java: Introspection vs Reflection

-   Reflection := Ability to introspect upon itself and manipulating internal properties of the progam.
    -   e.g. retrieve names of all methods of a class.
-   Introspection := Ability to examine types and properties at runtime
    -   e.g. a instanceOf check at runtime
-   Usually introspection is about testing a state, reflection is about manipulating the state
-   Even though reflection is a very powerful concept it usually comes with a lot of downsides
    -   you tie implementation details to concrete naming (also diffficult to refactor and anticipate side-effects)
    -   performance is bad
    -   read more [here](https://docs.oracle.com/javase/tutorial/reflect/index.html)

# 📅 20.07.2022 Gradle: How to find out the latest version available of your dependency

-   Either use a plugin like [gradle-versions-plugin](https://github.com/ben-manes/gradle-versions-plugin)
-   or check in the gradle file for the dependency repository (`repositories{}`) and look at their website which usually provides a search interface
    -   [Maven Central](https://search.maven.org/)
    -   [Google Maven Repo](https://maven.google.com/)

# 📅 19.07.2022 Gradle: Continuous build

-   Gradle allows to watch for changes and trigger specified task on changes again with
-   `gradle -t <task>`: watch for changes and retrigger task on e.g. file changes
-   you can also use `--continuous` instead of `-t`
-   [source](https://docs.gradle.org/2.5/userguide/continuous_build.html)

# 📅 19.07.2022 Api: On status codes 200 vs 204 (No-Content)

-   When the call was successful but there is no content you can use `204` e.g. used when sending a `PUT` request

# 📅 18.07.2022 InfoSec: False positives in dependency OWASP checker

-   OWASP dependency check is scanning dependencies based on a CVE which is associated with several CPE\'s, that CPE (similiar to a regex) is sometimes not well defined matching dependencies which are not related
-   Common Platform Enumeration (CPE) := A industry standard to define a specific hardware or software component.
    -   `cpe:/o:redhat:enterprise_linux:3:ga:desktop`
-   Common Vulnerabilities and Exposures (CVE) := Publicly known vulnerabilities and exposures, maintained by NFC.
-   Common Weakness Enumerations (CWE) := Categorizes types of software vulnerabilities, looking for the cause.
    -   examples for CWE\'s are for example cross-site scripting, race condition, buffer overflows
    -   in contract CVE\'s looks at the symptoms
    -   CWE\'s themselves are again categorized in the OWASP TOp 10
-   you can check for the exact matching reason on `build/reports/dependency-check-report.html` once you run `gradle dependencyCheckAnalyze`
-   reading [more](https://jeremylong.github.io/DependencyCheck/general/suppression.html) about it and also how to [read the report](https://jeremylong.github.io/DependencyCheck/general/thereport.html)

# 📅 18.07.2022 Chrome: Switch to left/right tab

-   `Ctrl + ⇧Shift +Tab↹`: Switch to left
-   `Ctrl + Tab↹`: Switch to right

# 📅 15.07.2022 Pattern: Why should you not validate on an outgoing request DTO

-   **good idea when**: if you always have the most up-to-date api definition of the provider you send a request to and callouts are expensive. Allowing you to instantly assume that clients returns a Bad Request
-   **bad idea when**: but once calling site has a older version being more restrictive than the up-to-date provider definition, the validation is neither in the interest of the calling site (otherwise you would just validate the incoming request dto or check invariants in code) nor for the provider site
    -   Example: consumer is failing on required field, provider would not because it is now optional
-   **bad idea when** the calling site is a pass-through application (see \'dumb pipelines\')

# 📅 14.07.2022 Java: Manually validate fields of DTO e.g. @NotBlank fields

``` {.Java}
import javax.validation.Validator;
Validator validator = Validation.buildDefaultValidatorFactory().getValidator();
Driver driver = new Driver();
driver.setAge(16);
Set<ConstraintViolation<Driver>> violations = validator.validate(driver);
```

-   see also [here](https://reflectoring.io/bean-validation-with-spring-boot/#validator)

# 📅 13.07.2022 Vim: Format function body

-   `vi}=`

# 📅 12.07.2022 Java: Reading ressource files relative to src folder of class

``` {.Java}
getClass().getResourceAsStream("/file_located_in_ressource_folder.json")
```

-   here it is important that file will be loaded from the target/build folder, so if you do not build your project files won\'t be copied over into the target folder

# 📅 12.07.2022 IntelliJ: How test run configurations work

-   How does IntelliJ ensure that a certain maven/gradle lifecycle is run before the rests are execuuted?
-   For every run configuation usually a build phase is executed before the launch of the actual run
    -   Click on a test class to be executed and run the tests \| Edit Run Configuration \| Modify Options \| Before Lunch \| Add before lunch task
    -   this ensure e.g. that all classes are compiled before a test is executed

# 📅 12.07.2022 IntelliJ: Set breakpoint on exception in debug mode

-   Go to: Run \| View Breakpoints \| Exception Breakpoints (Language specific)

# 📅 12.07.2022 Vim: Prepend newline before pattern match

-   `:%s/\./\0\r/g`: Adds a new line before each `.` in line

# 📅 08.07.2022 Maven: Lifecycle

-   when you run `mvn install` you trigger the following steps (see [lifecycle](https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html)):
    -   `process-resources`
    -   `compile`
    -   `process-test-resources`: here all files/folders are copied over from test ressources into target folder `test-classes`
    -   `test-compile`
    -   `test`
    -   `package`
    -   `install`
    -   `deploy`
-   Parameters
    -   `-DskipTests=true`: skips tests
    -   `-U`: forces a check for updated releases and snapshots on remote repositories

# 📅 08.07.2022 Eventual consistency

-   Eventual consistency := Eventually reflecting the same data in a distributed system.
    -   usually fast
-   Strong consistency := Always reflecting the same data in a distributed system.
    -   usually comes at the price of higher latencies
-   Examples
    -   queues: you never now when a message is consumed/ consumer is notified by a updated state
    -   data syncronzation between two db\'s: depends when sync run is
-   In such situations you usually want to have some reconciliation processes in place ensuring that the data is in sync

# 📅 30.06.2022 Consulting: Talking about velocity

-   *Person 1 : Your team is slow.*
-   *Person 2 : Slow, compared to what?*

# 📅 29.06.2022 Windows: Layout if second screen is not next up on top of primary screen

-   in display settings you can simply graphically move the physical location of each screen
-   if you move the secondary monitor on top of the primary you simply need to break through the top margin of the primary screen to get to the secondary one

# 📅 29.06.2022 Windows: Move current window to different screen

-   `Windows + Shift + Left Arrow`

# 📅 28.06.2022 Fun: 36 Methods of Mathematical Proof

-   ([source](http://jwilson.coe.uga.edu/EMT668/EMAT6680.F99/Challen/proof/proof.html))
-   **Proof by obviousness**: \"The proof is so clear that it need not be mentioned.\"
-   **Proof by general agreement**: \"All in favor?...\"
-   **Proof by imagination**: \"Well, we\'ll pretend it\'s true...\"
-   **Proof by convenience**: \"It would be very nice if it were true, so...\"
-   **Proof by necessity**: \"It had better be true, or the entire structure of mathematics would crumble to the ground.\"
-   **Proof by plausibility**: \"It sounds good, so it must be true.\"
-   **Proof by intimidation**: \"Don\'t be stupid; of course it\'s true!\"
-   **Proof by lack of sufficient time**: \"Because of the time constrait, I\'ll leave the proof to you.\"
-   **Proof by postponement**: \"The proof for this is long and arduous, so it is given to you in the appendix.\"
-   **Proof by accident**: \"Hey, what have we here?!\"
-   **Proof by insignificance**: \"Who really cares anyway?\"
-   **Proof by mumbo-jumbo**: Mumbo-Jumbo
-   **Proof by profanity**: (example omitted)
-   **Proof by definition**: \"We define it to be true.\"
-   **Proof by tautology**: \"It\'s true because it\'s true.\"
-   **Proof by plagarism**: \"As we see on page 289,...\"
-   **Proof by lost reference**: \"I know I saw it somewhere....\"
-   **Proof by calculus**: \"This proof requires calculus, so we\'ll skip it.\"
-   **Proof by terror**: When intimidation fails...
-   **Proof by lack of interest**: \"Does anyone really want to see this?\"
-   **Proof by illegibility**: asdasvasd233ef
-   **Proof by logic**: \"If it is on the problem sheet, it must be true!\"
-   **Proof by majority rule**: Only to be used if general agreement is impossible.
-   **Proof by clever variable choice**: \"Let A be the number such that this proof works...\"
-   **Proof by tessellation**: \"This proof is the same as the last.\"
-   **Proof by divine word**: \"...And the Lord said, \'Let it be true,\' and it was true.\"
-   **Proof by stubbornness**: \"I don\'t care what you say- it is true.\"
-   **Proof by simplification**: \"This proof reduced to the statement 1 + 1 = 2.\"
-   **Proof by hasty generalization**: \"Well, it works for 17, so it works for all reals.\"
-   **Proof by deception**: \"Now everyone turn their backs...\"
-   **Proof by supplication**: \"Oh please, let it be true.\"
-   **Proof by poor analogy**: \"Well, it\'s just like...\"
-   **Proof by avoidance**: Limit of proof by postponement as it approaches infinity
-   **Proof by design**: If it\'s not true in today\'s math, invent a new system in which it is.
-   **Proof by authority**: \"Well, Don Knuth says it\'s true, so it must be!\"
-   **Proof by intuition**: \"I have this gut feeling.\"

# 📅 27.06.2022 InfoSec: Risk responses / risk treatments

-   usually part of a risk managment plan (enumerating risks with likelihood)
-   4 classic ways of dealing with risk
    -   **avoid** risk e.g. not building the new feature or cutting of centrifuges inustrial controlls from the internet (stuxnet)
    -   **contain**, reduce impact when it happens e.g. frequent database backup
    -   **mitigate**, close the loopwhole
    -   **accept**, choose to move ahead e.g. do not protect internal tool since it is not exposed to the public internet and there is a low probabiliy to be attacked

# 📅 27.06.2022 InfoSec: How to decide on priority when it comes to brainstorming threats in a Threat Modelling session?

-   Usually, priority = impact \* probability
-   probability is super hard to estimate for average team members because
    -   we are all biased and have trouble evaluating risk
    -   confirmation bias := did we also consider evidence which speaks against our ideas?
    -   optimism bias := causes someone to believe that they themselves are less likely to experience a negative event
-   **better**,
    -   \(1\) guess how invested, elaborate the attack needs to be in order to suceed. Is it reasonable that the attacker goes through that effort?
    -   \(2\) with that information go to the PO/BA\'s and ask what a attacker looks like, and how motivated would they be to achieve a certain goal
-   if the effort is very low (e.g. can be exploited by an automated attack), then probablity is very high e.g. bot scanning for open ports
-   probability can be also phrased as, has this been see in the wild before?

# 📅 27.06.2022 InfoSec: Privacy

-   What is privacy?
    -   Legal definition: e.g. Gdpr
    -   Scientific definition
    -   Social/cultural definition
-   privacy issues only come up if it was not tolerated e.g. revenge porn
-   bossware := software or security design which aims to surveil employees (in non-consensual ways)
-   Datensparksamkeit vs Datenreichtum: the less data you collect, the less you need to protect
    -   is a continuum with decreasing usefulness raw data -\> information context -\> pseudonymized -\> anonymized -\> ereased data
    -   how to find the right balance? Start with strongest protection and loosen over time
-   Perfect privacy := Attacker with perfect background knowledge and unbound compute-power is unable to distinguish anything about an individual, uniformily accross users even in the worst-case scenario
    -   this is never possible, just privacy theory
-   Perfect secrecy := System can never be broken, even with unlimited computing power
-   Homomorphic encryption := Encrypted computation, you can process data without decrypting it
-   Federated computing := Data stays on local devices

# 📅 27.06.2022 InfoSec: How to be a good security champion?

-   Go through Checklists/Assesments
-   What data are we handling?
    -   PII, public, confidential, logs, tokens, secrets
-   Awareness, including to update onboarding docs, incident response plan
-   Do Threat Modelling sessions
-   Set goals for the team
    -   outside expectations? Company policies?
    -   Gaps from previous assessment?

# 📅 24.06.2022 Git: Search through commit messages

-   `git log --grep "message".`

# 📅 24.06.2022 Git: Stash and pop automatically when rebase

-   `git rebase origin/master --autostash`

# 📅 23.06.2022 Gradle: Implicit transparency when providing subtasks

-   When following dependency graph of task is given

``` {.text}
Some generic task A has a direct dependency on taskB and taskD (usually denoted by ~dependsOn~)
    taskA > taskB > taskC
    taskA > taskD
```

-   in order to make sure which of the dependent tasks run first we specify a `mustRunAfter`
-   implicit transparency becomes an issue if for instance we specifiy `tasks.findByName('taskD').mustRunAfter 'taskB'`
    -   the consequences are not intended because it will likely happen that taskD is run before taskC since it is only waiting for taskB
    -   Usually a warning is given by gradle, see [here](https://docs.gradle.org/7.4.2/userguide/validation_problems.html#implicit_dependency)

# 📅 23.06.2022 Gradle: Add replace string in file (hacky)

-   Gradle allows for replacing contents of the files in a copy process
-   we therefore first copy something in a tmp folder, delete the original file and then copy it back

``` {.groovy}
task _introduceChange(type: Copy) {
    from ('src/../') {
        include 'TargetClass.java'
    }
    into 'src/../tmp'
    filter { line -> line.replaceAll('TO_BE_REPLACED', 'REPLACEMENT') }
}

task _rmOrigin(type: Delete) {
    delete 'src/../TargetClass.java'
    followSymlinks = true
}

task _rmTmp(type: Delete) {
    delete 'src/../tmp'
    followSymlinks = true
}

task _copyBack(type: Copy) {
    from ('src/../tmp') {
        include 'TargetClass.java'
    }
    into 'src/../'
}

_introduceChange.finalizedBy _rmOrigin
_rmOrigin.finalizedBy _copyBack
_copyBack.finalizedBy _rmTmp
```

# 📅 23.06.2022 Gradle: Import groovy helpers into gradle script

``` {.groovy}
apply from: 'utils.gradle'
```

# 📅 23.06.2022 Gradle: Define several task dependencies inside a task

``` {.groovy}
task someTask {
    dependsOn build
    dependsOn clean
    tasks.findByName('clean').mustRunAfter 'build'
}
```

# 📅 21.06.2022 Docker Compose: Add container name to reference container from `docker`

``` {.yaml}
version: '3'
services:
  app: # this is the service name, only docker compose knows this
    build: .
    ports: [12345:8990]
    container_name: my-app # this is the container name, also docker can handle this
```

# 📅 20.06.2022 Docker: Hack for entrypoint to keep container running

-   `tail -F anything`: Will never terminate since it is waiting for file \'anything\' to appear

# 📅 20.06.2022 Gradle: Create task, ignoring exit value and print errors

``` {#Gradle Cli task .Bash}
task cliTask(type: Exec) {
    workingDir "${buildDir}"
    ignoreExitValue = true
    def stdout = new ByteArrayOutputStream()
    standardOutput = stdout
    errorOutput = stdout
    commandLine 'echo' 'hey'
    doLast {
        println stdout.toString()
    }
}
```

# 📅 16.06.2022 Workshop: How to plan out a workshop (or retro)

-   \(1\) Think of the different stages of the **process**
    -   Example: 1) Reflect on past 2) extract learnings 3) think of future 4) anticipate based on learnings what might help to make it better
-   \(2\) Think which **metaphors** you want to use in each stage (incl. overarching metaphor)
-   \(3\) Think of which **methologies** you want to use in each step
    -   Example: 1) Small warmup game 2) Brainstorming in group -\> Vote on Top-3 3) Discussion in small groups 4) Quick presentation

# 📅 14.06.2022 Gradle: See how long each build steps takes

``` {.Bash}
gradle --profile
```

-   outputs html

# 📅 14.06.2022 Team: Servant leadership

-   [source](https://asana.com/resources/servant-leadership)
-   Not mission but employee is the main focus
-   TBD: Explain some of the characteritics

```{=html}
<p align="center"><img height=400 src="https://raw.githubusercontent.com/biocarl/img/master/servant_leadership.png" /></p>
```
# 📅 14.06.2022 Git: Revert last n commits in one commit

``` {.Bash}
git revert --no-commit HEAD~3..
git commit -m "Revert of last 3 commits"
```

-   only working if not merge commit present in the commits to be reverted

# 📅 13.06.2022 microservice: Pattern Index from book *Monolith to Microservices* **Splitting the monotlith**

-   Branch by abstraction: Coexisting two implementations of the same functionality in the same codebase at the same time, allowing for a new implementation to be incrementally developed until it can replace the old implementation. (p.104)
-   Decorating collaborator: Trigger functionality running in a separate microservice by sniffing requests sent to the monolith, and the responses that are sent back in return. (p.118)
    -   also can be used without touching the monolith
    -   similiar to stranger fig but original request is still passed down to the monolith
    -   response or request of monolith is extended by a microservice e.g. adding a new field
-   Strangler fig application: Wrap your new microservice architecture around the existing monolith. Calls to use functionality that has ben migrated from the monolith to your microservices are diverted; other calls are left unchanged. (p.79)
    -   intercepting inbound call through proxy (even protocoll can change) or redirect
    -   (+) you do not need to touch the monolith
    -   does not work when calls are inside the monolith and not at the boundary
    -   you can still call back to the monolith if this allows for smaller steps of extraction
-   Parallel run: Run two implementations of the same functionality side by side, to ensure that the new functionality behaves appropriately (p.113)
-   UI composition: Presenting a single user interface by assembling many small parts together (p.89)

**Decomposing the database**

-   Aggregate exposing monolith: Exposing domain aggregates from a monolith to allow microservices to access entities managed by the monolith. (p.138)
-   Change data capture: Transmit changes made to an underlying datastore to other interested parties. (p.120)
    -   usefull when call can\'t be intercepted or when the needed data is not exposed via an api
    -   CDC can be done e.g. with a log-based approach
-   Change data ownership: Moving the source of truth from the monolith to a microservice. (p.141)
-   Database as a Service interface: Using a dedicated database to provide read-only access to internal service data. (p.136)
-   Database view: A view is projected from an underlying database, allowing for parts of the database to be hidden. (p.128)
-   Database wrapping service: A facade service is placed in front of an existing shared database, allowing for services to migrate away from direct use of the database. (p.132)
-   Dedicated reference data schema: A dedicated database to house all static reference data. This database can be accessed by multiple different services. (p.181)
-   Duplicate static reference data: Copy static reference data into microservice databases. (p.179)
-   Monolith as data access layer: Accessing data merged by monolith via APIs rather than directly accessing the database.
-   Move foreign-key to code: Move management and enforcement of foreign-key relationships from a single database up into your service tier. (p.173)
-   Multischema storage: Managing data in different databases, typically while migrating a shared database to a database-per-service model. (p.171)
-   Repository per bounded context: Break apart a single repository layer ariund different parts of the domain, making decomposition into services easier. (p.162)
-   Shared database: A single database shared between more than one service (p.125)
-   Split table: Breaking a table into two parts prior to service decomposition (p.171)
-   Static reference data library: Move static reference data into a library or configuration file that can be packaged with each microservice which needs it (p.182)
-   Static reference data service: A dedicated microservice that provides access to static reference data. (p.184)
-   Synchronize data in application: Syncroniye data between the sources of truth from inside a single application (p.143)
-   Tracer write: Incrementally migrate data from one source to another tolerating two sources during the migration (p.149)

# 📅 13.06.2022 Pattern: \"Keep the pipes dumb, the endpoints smart\" - Martin Fowler

-   dumb pipelines := the transport of messages between two microservices really is not doing nothing as delivering the message (e.g. no eleborate logic (like validations) in proxy, api gateway etc.)
-   smart endpoints: means that all logic (like validations etc.) resides in the microservice behind a endpoint
-   this is the opposite to the concept of Enterprise Service Bus (EBS), which are very smart pipes intercepting calls and taking care of things like security checks, Routing. business flow / validation and transformation
-   What is the motivation behind this?
    -   Higher cohesion, less coupling between components (e.g. change in complicacted proxy might impact a lot of downstream services)
    -   delivery contention (see Sam Newman): a lot of teams modifying the same component

# 📅 10.06.2022 Transparent remoting and location transparency

-   Transparent Remoting: is about making remote calls look like local calls (with proxies forwarding to remote server)
    -   you never know whether the methods are executed locally or the data has been sent over the network to be executed on a remote object
    -   but this is still a cheap illusion since you can not abstract away issues like latency, memory access, partial failure and concurrency
    -   Example: Java Remote Method Invocation (RMI)
-   Location transparency: is about making all calls (including local ones) look like remote calls
    -   so assume that all those networking issues can occur making this transparent right from the start
    -   physical location does not matter only the identifier

# 📅 08.06.2022 wiremock: When you want to mock server response behavior, example for spring rest template

-   [Wiremock](https://wiremock.org/docs/junit-jupiter/)

``` {.Java}
@WireMockTest
class WiremockTest {

    @Test()
    void test(WireMockRuntimeInfo wmRuntimeInf){
        String endpoint = "/someEndpoint";
        stubFor(post(endpoint).willReturn(
              aResponse()
                .withResponseBody(new Body("{}"))
                .withStatus(200)
                .withFixedDelay(2000) //simulates delay if you set timeout in restTemplateBuilder accordingly
                .withHeader("Content-Type", "application/json")));  
        final ResponseEntity<ResponseClass> response = restTemplate.exchange(
                        wmRuntimeInfo.getHttpBaseUrl() + "/" + endpoint,
                        HttpMethod.POST,
                        new HttpEntity<>(request, headers),
                        responseType);
    }
}
```

# 📅 08.06.2022 Mockito: Inject real autowired beans

``` {.Java}
@Spy
private SomeService service = new RealServiceImpl();
@InjectMocks
private Demo demo;
```

-   this becomes especially useful if you do autowire in the depenend class and can\'t inject mocks via the constructor (this sometimes makes sense if you do not want a complicated constructor for child classes)

# 📅 20.05.2022 Workshop: Nobody is perfect

-   Put a question nobody can know the answer to, everyone has to put in a anonymous answers and everyone is voting what is the most realistic answer. The game master is also adding the real answer
-   The most voted answer get points
-   is also a game with the same name (Ravensburger)

# 📅 17.05.2022 JUnit: Assert fields on thrown exception

``` {.Java}
Throwable thrownException = assertThrows(NullPointerException.class, () -> {
    testedMethodThrowingException();
});
assertEquals(thrownException.getCode(), HttpStatus.UNPROCESSABLE_ENTITY.value());
```

# 📅 12.05.2022 Pattern: Port and Adapters aka Hexagonal Architecture

-   [source](https://alistair.cockburn.us/hexagonal-architecture/)
-   **Intent**: You want to be able to run the application independent of \'users, programs, automated test or batch scripts\' and test in isolation from its infrastructure
    -   no leaking business logic into UI layer
    -   easier to test (no mocking required)
    -   easier to move from a UI driven system to a batch-process
-   Shift of mindset: \"Rule to obey is that code pertaining to the \'inside\' part \[of the application\] should not leak into the \'outside\' part.\"
    -   you do not think about your application any more
        -   like incoming request from left to right
        -   layers from top to down
    -   you often have several incoming/outgoing flows, easier to model with inside/outside and clearer to enforce that nothing should leak outside
    -   also read on this [Data on the Outside versus Data on the Inside](http://www.cidrdb.org/cidr2005/papers/P12.pdf)
-   **How**: All outgoing and incoming requests have to go through a port which then converts the information (with an adapter) in a format which is compatible with the technology on each side. That leaves the application completely isolated and pure from it\'s infratstructure or UI
-   Why is it called port?
    -   use the same logic as a port from a OS, any device with a fitting protocol can plugin in
    -   protocol of that port is an API, whereas the adapter converts the API to signals which are needed by the two connecting sides
    -   Example: Database connecting to port needs adapter which either converts signal into SQL, filestream or adapter to a mock-database

# 📅 12.05.2022 Pattern: Application Layering

-   What do we want to achieve with layering?
    -   domain layer should not depend on low-level concerns (aka. dependency inversion)
    -   avoid anemic domain models
    -   high-level folders should denote domain concerns, not technical ones
-   What to watch out for
    -   avoid using modules for seperating out layers: this just creates pain (see also [screaming architecture](https://blog.cleancoder.com/uncle-bob/2011/09/30/Screaming-Architecture.html))

# 📅 12.05.2022 Pattern: Saga-Pattern - Part II

-   Origin from even before microservices: Splitting up long-running transactions (because they were blocking ressources for too long)
-   Type: Orchestration (like command & controll)
    -   state is centralized
    -   typically use syncronous request/response to communicate that transaction was successful (but also event-based is possible)
    -   disadvantage
        -   a lot of coupling with controller (really do not use if you have multiple teams responsible for the microservices)
        -   business logic can leak into controller
-   Type: Choreography (Trust and Verify)
    -   only communictate state as event (relevant services listen to that topic)
    -   disadvantage
        -   difficult to understand whole business process
        -   difficult to see whole state
-   You can also combine both approaches
-   How to handle failures
    -   do not use to resolve technical errors (should only be used for business error)
        -   here should use retries, circuit breakers instead -\> system should be stable before introducing Saga patterns
        -   further reading [here](https://www.ufried.com/blog/limits_of_saga_pattern/)
    -   backward-recovery: revert what happened before
        -   compensating transactions (e.g. remove entry from db)
            -   you sometimes also want to keep track of those compsensations, that they happened
    -   foreward-compensate: just retry and do not compensate for it
-   Alternatives to Saga patterns: Two-Phase commits

# 📅 12.05.2022 Java: Creating custom annotations

-   for class level annotation

``` {.java}
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.TYPE)
public @interface CustomAnnotation {
    //...
}
```

# 📅 12.05.2022 Gradle: Share config between to different tasks

``` {.groovy}
def commonConfig = {
    classpath = sourceSets.main.runtimeClasspath
    jvmArgs "-Xmx1024m", "-XX:MaxPermSize=128m"
}

task runSomething() {
    configure commonConfig
}
```

# 📅 11.05.2022 Gradle: Managing gradle dependencies

-   Get to know which version a dependency has and the decision for it (see Dependency mediation)
    -   `gradle dependencyInsight --dependency package_name`

# 📅 11.05.2022 Workshop: More tech/developer experience orientated healthcheck

-   source is from spotify ([source](https://engineering.atspotify.com/2014/09/squad-health-check-model/))
-   **Support**: Getting support and help when asked for it
-   **Value**: Feeling about what has been delivered so far
-   **Fun**: Excitement about work & working together
-   **Health of Codebase**: Cleanliness, easy to read, test coverage..
-   **Learning**: New vs. old stuff
-   **Mission**: Clear & inspirational
-   **Pawns or Players**: Fate in own hands (decide what to build and how)
-   **Speed**: Development, waiting times, delays
-   **Process**: Ways of working
-   **Teamwork**: Bunch of individuals vs. team.

# 📅 10.05.2022 Mockito: Fundamentals

-   Initalize by

``` {.java}
import static org.mockito.MockitoAnnotations.openMocks;
openMocks(this);
// or by
import static org.mockito.MockitoAnnotations.initMocks;
initMocks(this);
```

-   Use captor for checking which values were passed

``` {.java}
@Captor ArgumentCaptor<OriginalClass> originalInstance;

//later in test
 when(someInstance.do(originalInstance.capture());
 assertEquals(...,originalInstance.getValue());
```

-   You can chain when commands for specifiying mock behavior on first, second, 1+n call

``` {.java}
when(myMock.doTheCall())
   .thenReturn("You failed") //first call
   .thenReturn("Success"); //second call
```

-   How to use verify (more on this [here](https://www.baeldung.com/mockito-verify))

``` {.java}
// test that mock method was called
List<String> mockedList = mock(MyList.class);
mockedList.size();
verify(mockedList, times(1)).size();
// test that no method was called on mock
verifyNoInteractions(mockedList);
```

-   When to stub and when not? Usually don\'t stub pojos

*Usually you want to test your code with real inputs and expected outputs and usually these will be data structures or pojos.* - [source](https://softwareengineering.stackexchange.com/a/363127)

# 📅 09.05.2022 Spring: Get request context to retrieve things like headers globally

-   Each request is served in a single threat which contains the request context
-   If not needed outside of controller, you can obtain headers via `@RequestHeader` annotation

``` {.java}
String retrieveHeaderFromRequest(){
    Optional<RequestAttributes> requestAttributes = Optional.ofNullable(RequestContextHolder.getRequestAttributes());
    if (requestAttributes.isPresent()) {
        String headerField =
            ((ServletRequestAttributes) requestAttributes.get()).getRequest().getHeader("headerName");
        if (headerField != null && !headerField.isEmpty()) {
        return Optional.of(headerField);
        }
    }
    return Optional.empty();
}
```

# 📅 09.05.2022 Spring: Interceptors 101

-   when to use: cross-cutting concerns
-   Spring Rest Templates allows to specify interceptors to modify request before it is sent ([source](https://programmer.group/spring-resttemplate-uses-interceptors-to-configure-http-request-headers.html))

``` {.java}
@Component
public class CustomInterceptor implements ClientHttpRequestInterceptor {
  @Autowired
  CustomCounter counter;

  @Override
  public ClientHttpResponse intercept(HttpRequest request, byte[] body, ClientHttpRequestExecution execution)
      throws IOException {
     // modify header
    HttpHeaders headers = request.getHeaders();
    headers.add("actionId", counter.nextInt());
    // forward request
    return execution.execute(request, body);
  }
}
```

# 📅 06.05.2022 Workshop: City-Retrospective

-   Icebreaker: Which city is best for some certain activities?
    -   List of Cities and symbols to vote on: party, nature, food, bicycle, architecture
-   Check-In: Traffic light, green, red, yellow for safety
-   Brainstorming: Traffic jam? neighborhoods? urban gardening?
-   Action items: Let\'s make our city better

# 📅 03.05.2022 InfoSec: Terms in Security

-   VicSocks := victim sockets, malware opening a socket on victims maschine to use their IP for malicious activity
-   Credential Stuffing := Instead of bruteforcing a system with random credentials a password dump from previous breaches is used
    -   Mitigations
        -   2FA
        -   block IP\'s (but usefull if attacker used e.g. VicSocks)
        -   check against password dumps and request to change passwords
        -   Google Capture

# 📅 28.04.2022 Networking: Firewalls 101

-   on OSI layers 3-4
-   IP, port, access controll list

```{=html}
<!-- -->
```
-   Web Application Firewall (WAF)
    -   on OSI layers layer 5-7
    -   designed to protect against higher level attacks e.g. from OWASP Top 10
        -   for example http flood attack or slowloris
        -   legitimate web requests, not attacking network but application itself
    -   example: http flood atack
        -   it is very difficult to distinguish them from legitimate traffic, eventually resulting in DoS for the real users
        -   a WAF for instance would keep track of malicous IP\'s dynamically and block those once a certain pattern in requests is identified

# 📅 28.04.2022 Networking: OSI Model 101

-   OSI := open systems interconnection, is a communication standard between computers
-   when OSI layer is used
    -   characterizing network issues
    -   categorizing cyber threats
-   split up in 7 layers
    -   Layer 7 (Application): *All the common protocolls like HTTP, FTP, TELNET, SMTP*
    -   Layer 6 (Presentation): *Responsible for converting incoming data so that the application understands its content and translating outgoing data so that it conforms to the protocoll standard. This also includes things like encryption, and compression of data*
    -   Layer 5 (Session): TBD
    -   Layer 4 (Transport): TBD
    -   Layer 3 (Network): TBD
    -   Layer 2 (Data Link): TBD
    -   Layer 1 (Physical): TBD

# 📅 28.04.2022 JUnit: Tags

-   helps you to filter for certain annotated tests (include/exclude)
-   Use `@Tag` on either class or method level
-   in Maven Surefire Plugin use:

``` {.xml}
<configuration>
        <groups>group3</groups>
</configuration>
```

in mvn use: `mvn test -Dgroups=group3,group2`

# 📅 28.04.2022 Infrastructure: Open Policy Agent (OPA)

-   [source](https://www.openpolicyagent.org/)
-   you define policies and a agent is checking them (compliance)
-   e.g. use terraform plan json output and feed it into agent

# 📅 28.04.2022 QA: Synthetic monitoring

-   a small subset of tests you execute on your prod environment in a regular fashion and create alerts on it
-   sometimes called semantic monitoring
-   can be combined with canary releases
-   **why**: System-wide e2e tests without coupling the deployment of microservices
-   **how**: canary data you sent through the system (but side-effects are avoided)
    -   you would still would want to write all the synthetic data in db but clean up after the test
-   usually quite expensive to implement system-wide
-   [further reading](https://martinfowler.com/bliki/SyntheticMonitoring.html)

# 📅 26.04.2022 QA: Performance tetsing of microservice in isolation vs system-wide tests

-   Benefits of testing system in isolation
    -   see if changes you introduced decrease performance
    -   since you test system in isolation you can benchmark against a baseline (regression-testing)
-   Benefits of doing a system-wide performance test
    -   also see other system restrictions
    -   also discover things like race-conditions
-   It often makes sense to do both but the question how often and when you run those
    -   e.g. running system in isolation you could do on every deploy and system-wide on every release

# 📅 26.04.2022 Maven: Maven Enforcer Plugin

-   like a unit test for maven files
    -   built-in rule: Dependency Convergence
        -   fail if two dependencies A,B depend on a different version of another dependency C
        -   Maven usually falls back to the latest version (see also Dependency mediation)
-   Dependency mediation
    -   Maven/Gradle always has to set for one version otherwise we would get a scope conflict (same class names etc.)

# 📅 26.04.2022 Maven: Multi-Module project

-   Define root and module poms

``` {.xml}
<!-- In root pom -->
<modules>
    <module>core</module>
    <module>service</module>
    <module>webapp</module>
</modules>
<!-- In module pom -->
<parent>
  <artifactId>parent-project</artifactId>
  <groupId>com.baeldung</groupId>
  <version>1.0-SNAPSHOT</version>
</parent>
```

-   Dependency Management in Parent Project ([source](https://www.baeldung.com/maven-multi-module))
    -   centralizing the dependency information in one place
    -   in parent pom you define artifact, groupId and version
    -   in inheriting pom only artifact, groupId
    -   exclusions are also inherited

# 📅 25.04.2022 Java: Memory management Shown my Native Memory Tracking

-   Heap: Java objects
    -   globally accessable
-   Non-Heap
    -   Garbage Collector: GC requires memory for data structures and algorithms to do its job
    -   Code Cache: Storage of dynamically generated code
    -   Compiler: JIT compiler needs some memory to run
    -   Metaspace
        -   here Class metadata (method bytecodes, symbols, constant pools, annotations) is stored
    -   thread stack
        -   contain references
        -   last-in, first-out (LIFO) memory allocation
        -   each thread contains at least 1 stack
            -   Java stack (Java method calls)
            -   Native stack (Native method calls in VM)
-   Other: For example native C code
-   Debug Out-Of-Memory Errors

``` {.bash}
# Print out heap dump
-XX:+HeapDumpOnOutOfMemoryError
# Native Memory Tracking
-XX:NativeMemoryTracking=summary -XX:+UnlockDiagnosticVMOptions -XX:+PrintNMTStatistics"~ for advanced tracking
# Limit stack size
-Xss1M # to set the maximum of stack size to 1M
# Limit heap
 -Xmx
# Limit percentage of total RAM but only for heap (!)
 -XX:MaxRAMPercentage
```

# 📅 25.04.2022 Team: Meeting rules

-   👥: Team and 👩‍🏫: Facilitator
-   Before the meeting
    -   👩‍🏫 Before sending out the invite go through the 7Ps below and put relevant information in the invite (like outcome and preparation)
    -   👩‍🏫 Use the optional functionality for participants
    -   👩‍🏫 When the meetings includes some kind of discussions create a Mural/Miro/Jamboard in advance
    -   👩‍🏫/👥 Do you want to ask someone to help you out with creating meeting notes?
    -   👥 Accept/reject meeting asap so that the facilitator can plan accordingly
    -   👥 Do preparation required of the meeting
    -   👥 When in doubt, request a purpose, product and suggested process
-   During the meeting
    -   👩‍🏫 Give context to everyone participating in the meeting
    -   👩‍🏫 As the facilitator always come back to the outcome and push for tangible results
    -   👥 It is not the responsibility of the facilitator only to make this a productive meeting (everyone should limit scope and avoid rabbit holes)
-   After the meeting
    -   👩‍🏫 Create action items in the Daily Guide
    -   👩‍🏫 Update the Meeting notes and follow up with action items e.g. updating a LADR
    -   👥 Everyone should go through the meeting notes and provide comments if necessary.

# 📅 22.04.2022 IntelliJ: Shelve and unshelve changes

-   Like stashing a change list (creating a patch), which you can apply later again
-   this happens automatically in IntelliJ when you pull with changes in working dir

# 📅 22.04.2022 Jackson: Objectmapper for enums

-   Serialization: `@JsonValue`, indicates a single method that the library will use to serialize the entire instance. e.g. `toString()`
-   Deserialization : `@JsonCreator`, just out this on the constructor and specificy the primitives you want to create the object from

# 📅 21.04.2022 Networking: DNS server mappings are cached locally Working on Windows OS

-   `nslookup  <url>` does reach out to dns server to retrieve IP
-   `tracert <url>` goes same route as os, uses cache (not reaching out to dns server every time)
-   `ipconfig /flushdns` clear local cache
-   there is also a local dns lookup
    -   specified via Windows `c:\Windows\System32\Drivers\etc\hosts` file

# 📅 20.04.2022 Networking: Principle of Round Robin

-   Easy process for network/process schedulers to distribute load/data amongst workers etc.
-   Round-robin DNS: Principle applied on redundant DNS servers, like a load balancer

# 📅 19.04.2022 Networking: Fundamentals

-   `nslookup <url>`: Nameserver lookup, shows responding dns server for that url and the ip\'s it is resolving to
-   `route print` / `netstat -r`: Showing routing tables
-   `DNS server`: Responsible to translate domain names into IP adresses
    -   Recursive DNS server
        -   for dns lookup
        -   usually run by our internet service provider (ISP)
        -   **but** *when you connect to a Virtual Private Network (VPN), the DNS server of your VPN replaces the DNS server of your ISP*
    -   Authoritative DNS server
        -   hold official dns records for a domain
        -   provided by domain registrars
-   DNS servers can be configured differently, when queried for a domain they return a ...
    -   Static IP server e.g. for servers
    -   Dynamic IP server e.g. when devices are not permanently connected to the network
    -   Round Robin server, return a list of IP addresses, all being able to serve the request
    -   Load balancing server, return von IP address which can server request, load is distributed optimally
-   What do I see when I type in whatismyip on the internet?
    -   this is the IP the isp is assigning to my router, all devices connected to the router have the same IP adress
-   How can I have a different IP in my local network?
    -   each router has a *dhcp server* assigning local up\'s to all devices
    -   process:
        -   1.  New device is *broadcasting* (requesting IP), broadcast is sent to dhcp server and to all other devices

        -   1.  dhcsp has a ip range to choose a new ip from and sends it out to new device and all other other devices

        -   1.  new device with ip is sending out confirmation to dhcp and all other devices
    -   if local device (with local IP) wants to send a request to some server in the internet it needs a NAT
-   How are IP adresses assigned in a VPN network?
    -   in the same fashion, a vpn network also has a dhcp server
-   A network problem I\'ve encountered
    -   Your **ISP** / **router** settings either defaults to ipv6 or ipv4 (in my case ipv6)
    -   For domainA the **dns server** from the **vpn** gave back both ipv6/ipv4 addresses (with precedence to ipv6)
    -   since isp defaults to ipv6 the ipv6 is chosen for that domainA
    -   the problem is that the vpn is not supporting ipv6 and request to a ipv6 goes not through vpn but the internet
    -   resulting in not being able to access the website

# 📅 19.04.2022 InfoSec: Threat modelling

-   per definition you never have a complete thread modell
-   it is more about brainstorming possible causes to mitigate them, in reality a breach always consists of a combination of several threats
-   different kinds of threat modelling
    -   broad threats and thread sources: also understandable by non-tech people - identifying bad actors and their motivations
    -   technical threats and vulnerabilities
-   always include PO because they know about cruciality of data and business context
    -   *When cyber security losses occur they are business losses.*
-   *Threat modelling little and often*
    -   start with a thin slice, ideally what you are working on
    -   it is better to continously build up the threat modelling muscle
-   Examples of well scoped sessions (from [source](https://martinfowler.com/articles/agile-threat-modelling.html#ScopingTheSession))
    -   Scope in current iteration.
    -   An upcoming security sensitive feature, such as a new user registration flow.
    -   The continuous delivery pipeline and delivery infrastructure.
    -   A particular microservice and its collaborating services
    -   A high level overview of a system to identify security tech debt.
-   **Evil brainstorming**
    -   come up with ways to *attack, break and frustrate* a particular system
    -   Use STRIDE cards
-   **Learnings from running Threat Modelling session**
    -   Structure followed

        a\) Map out System (already prepared)

        -   give people the chance to add things
        -   ask questions
        -   always only things relevant to the scope (e.g. current feature played)

        b\) Label data

        -   Copy over system and add where data flows
        -   you can make different distinctions if they fall into different data categories
            -   PII, Non-PII, Financial data, Technical secrets, User secrets
            -   at-rest (persisted), in-flight (data just running through the system)

        c\) Do Evil brainstorming

        -   Copy over mapped system
        -   brainstorm together where a system could be hacked (according to STRIDE)

        d\) Rank according to Impact and Probability

        -   Two voting rounds and then arrange on magic quadrant

        e\) Coming up with action items (resulting in different outcomes)

        -   Add to tech depth
        -   Additional AC in stories
        -   Additional criteria to DoD
        -   new Story, Spike or Epic

        f\) Additionally you can also come up with low-hanging fruit (things which are easy to accomplish e.g. adding a health check)

# 📅 13.04.2022 Infrastructure: Jenkins 101
- [source](https://joostvdg.github.io/jenkins-pipeline/core-concepts/)

-   `Step`: A single task
-   `Built-In vs Agents`
    -   built-ins coordinating
    -   agents are doing the actual work (reasons: infosec/networking, different OS\'s)
-   `Workspace`
    -   should be cleaned up, tmp
    -   where artefacts are written out
-   `Stage`
-   `Sandbox and Script Security`
-   `Stash & archive`
    -   stash: forward results from one step to another (IO, CPU expensive)
    -   archive: expose artefacts over api/ui

# 📅 13.04.2022 Python: How to mock in python

-   Part of unittest (standard module in python)
    -   `from unittest import mock`
    -   `from unittest.mock import MagicMock`
-   If you want to mock a single method of an object: `@mock.patch.object(TheClassOfMethod,'the_method_to_mock', side_effect=returns_result_of_mocked_method)`
-   If you want to mock the whole object (and do not care about other overwritten methods):
    -   example for replacing request object and mock post method: `@mock.patch('requests.post', side_effect=returns_result_of_mocked_method)`
-   Difference between `side_effect` and `return_value`
    -   `side_effect`: provided method is called with orginal parameters on the object which is mocked
    -   `return_value`: mock method is called empty and return value is returned
-   Learning: When you pass in the mocked object into the test method, they are in reverse order of the patch annotations

``` {.python}
@mock.patch.object(ClassA, 'do1')
    @mock.patch.object(ClassB, 'do2')
    def test_something(self, mockB, mockA):
    mockA.assert_not_called()
    mockB.assert_called_once()
    self.assertEqual(mockB.call_count, 2)
```

# 📅 12.04.2022 Java: System.getProperty vs System.getenv

-   environment variables are just taken from the OS
-   properties are like start parameters you pass in into the jvm
-   usually prefer properties over environment variables because they are more specific in scope
    -   for environment variables you could always have another process in the same shell changing the behavior of your application

# 📅 12.04.2022 Maven: Testing with Maven

-   tests usually run with `maven-surefire-plugin`
-   you can set filters for including/excluding classes: `<includes> <include>**/*SpecialTest*.java</include></includes>`
-   set verbose logging (including debug) with `-X` on mvn command
-   scope test in maven is analogous to testImplementation in gradle

# 📅 12.04.2022 Java: Drawback of multi-module projects when libabries depend on a jvm

-   when you have a multi-module projects and run a test task on root level, the tests of the different modules are obvisouly spawned in several jvm\'s. When you have mechanism which relies on the fact that tests are run in the same jvm (e.g. pact interactions have to be all validated before results are published) you have to put those toegther in a separate module

# 📅 08.04.2022 Agile: Philosophy Kanban

-   Comes from Toyota where you have different steps in automanufacture workflow, you a high flow from one state to the other
-   At every state transition the card should move into a new process so e.g. Ready for development is not useful becaue it is just waiting there. Better to leave it in analysis and label it as ready
-   You also should not have a sign-off column because sign-off meeting should be part of the state change to be done. If you have no such column and stories are waiting longer in dev due to waiting for a meeting sheduled to it just makes the problem more visible and should be resolved

# 📅 08.04.2022 Maven: Compiling

-   if you have maven modules imported, compiling the dependent modules is not enough - you also have to package them
-   otherwise you might get some `NoClassDefFoundError`

# 📅 07.04.2022 Circuit breaker

-   If you have send many requests and get a lot of errors you pause requests right away to reduce load on the target system
-   it is difficult to decide when to allow requests again (increase limit)
-   e.g. Histrix
-   Different states: Open, Closed, Half-Open (probe if downstream system is ok again, low traffic)

# 📅 07.04.2022 Adaptive concurrency

-   [source](https://vikas-kumar.medium.com/handling-overload-with-concurrency-control-and-load-shedding-part-2-6b8b594d4405), [source~2~](https://netflixtechblog.medium.com/performance-under-load-3e6fa9a60581)
-   Netflix switched over from circuit breakers
-   capacity changes over time, calling services should adapt expected capacity automatically
-   you monitor congestion and calculate limit via algorithm
-   only works if all calling services implement this

# 📅 31.03.2022 The 12 Factor App

-   **Config**: Externalize all config from Code
    -   Config is everything that varies accross deploys (prod/staging/tenants), code not
    -   Never store constants in code for things like services adresses but externalize config
        -   via environment variables
        -   runtime configurator
    -   when you externalize do not group those configs into environment groups, combining those groups later adds a lot of complexity e.g. `joes_staging`
    -   Litmus test: At every point in time you could open source the project without giving away credentials etc.
    -   Motivation
        -   have crucial information (which might be used in other contexts) at a centralized place e.g. when service~url~ is changing
        -   you only have one artefact: Build once deploy anywhere
        -   It is faster: Change externalized config, no need to rebuild the image
        -   You do not mistakenly check in such config into source
        -   config is language independent

# 📅 30.03.2022 QA: Learnings on pact and pact broker

-   why to use tagging for feature toggles? ([read more on this](https://docs.pact.io/pact_broker/tags))
    -   on consumer side you have a feature toggle but you don\'t know if the provider already has the features implemented, integrated in the deployed artefact. That is why you want to tag with the consumer/provider version after deploying the artefact. You have a mapping between consumer versions of a contract and how this related to the deployed artefacts, helping you decide which feature toggles on the consumer side you can toggle on. The other way of doing it would be to check on the deployed artefacts which feature is present and which not but doing it this with the pact contracts is like putting a matching pattern over the codebase using the logic you already have set anyway for the contract testing
-   how does pending contracts work?
    -   motivation: You want to introduce a change as a consumer without immediately breaking the provider. The provider decides when to fufill the contract
    -   First you have a new contract version on consumer side, first you would introduce this as pending
    -   a pending contract never brakes the pipeline on provider side
    -   once the provider meets the requirements of the new contract the pending flag is removed
    -   if at another run the contract brakes on provider side the pipeline also breaks

# 📅 29.03.2022 Workshop: Airport metaphor

-   Icebreaker: Where do you want to go next?
-   Healthcheck: Check-In at airport
-   Action items: Take-Off
-   Brainstorming
    -   Learned: The scanner shows all
    -   Liked: Celebrate in the VIP lounge
    -   Disliked: What is hidden in the restricted area?
    -   Longed for: Where should we travel to?
-   Feedback: Stars with tripadvisor: From worst trip ever, I will do the next retro by myselves
-   Who is next: Stuart with sunglasses

# 📅 17.03.2022 Sensible practices

-   Trunk-Based development
    -   **Why**: Faster feedback, resolve merge conflicts quicker, easier to code review because smaller changes
    -   Prerequisite of Continuous Integration
    -   If not possible only very short feature branches
-   TDD
    -   **Why**: Simpler, just make the test pass. More modular code. Fast feedback - less debugging during development
-   Pairing
    -   **Why**: Fast feedback, shared ownership and knowledge transfer
-   Security first
    -   Scanning for vulnerabilities in pipeline (libs, container immages etc.)
    -   Secret manager
    -   Thread modelling part of agile routine
    -   Quick reaction strategies e.g. monitoring, fix-forward
    -   least privilege principle when it comes to access etc.
    -   Consider checklists like OWASP
    -   **Why**: Faster feedback and therefore impact on code and design, reproducable and therefore less dependent on security SME for audits etc.
-   Automated build pipeline
    -   within miniutes
    -   everyone has easy access to current state and should be informed in case of a failure
    -   prioritize speed and non-flakyness of pipeline
    -   **why**: quick feedback if new changes introduce defects, less efort because no manual steps
-   Automated deploy pipeline
    -   also automated infrastructure (e.g. terraform)
    -   manual approvement can happen but no manual steps
    -   (❗) artefact is build once and deployed to different environments with different configuration
    -   Avoid configuration drift in environments (different settings in infra)
    -   **why**: *Automation reduces errors caused by humans.* + faster feedback, less time required

Early and continuous deployment

-   Start early to deploy to prod so you do not hide the work like cfr\'s required to deploy to prod
-   also deploy components regulary even if there was no change to ensure that everything is still working
-   **why**: Early feedback and repeatability

# 📅 11.03.2022 - 17.03 Basics of DDD

-   Domain Model := Business logic, context etc. without any technical details (including persitence etc.). Everyone involved in the development lifecycle should use that language which was agreed on (helps avoiding translation errors)
-   Stategic vs Tactical design
    -   Strategic design is about what we build
    -   Tatical design is about how we build it
-   **Strategic design** (also for non-technical people)
    -   Goal: Go from problem space -\> \'as-is\' solution space -\> to better solution space: Question about the **what**
    -   What is the problem with several subdomains each having their own language
        -   in order to integrate with those subsystems you have to translate between different domains
        -   forces you to introduce even more new language to have a common understanding
            -   for the model this means it get quite complex and bloated when you want to account for each subdomain
        -   results in misunderstandings, tribe knowledge, slow on-boarding etc.
    -   the most subsystems (core domain) should be organized as a bounded context, where the language within is unambiguous
        -   the other subsystems are called generic, supporting subsystems
-   **Tactical design**
    -   how to organize your code, what tools to use
    -   Problem statement:
        -   Usually clients operate on entities (e.g. a service, controller enforcing business rules) leading to business logic which is spread out around the codebase
    -   Solution: Put everything in your domain model and expose business logic as public methods, no other methods allowed
    -   ❓ Put it to a extreme: Does this mean a strict DDD model should not have getters and setters?
    -   Terms
        -   **Entity**: Defined independently of properties, e.g. you, who can change over time
        -   **Value objects**: Identity defined entirely by its values e.g. color brown.
            -   always consider value objects over primitive types because you can encode business logic in them e.g. mass can\'t be negative
        -   **Aggregates**: Collection of entities or value objects
            -   important for enforcing buiness rules on several objects
            -   **Aggregate Root**: Most parent element of aggregate structure
                -   when you want to change a element in the structure you have to do this through a exposed method in the aggregate root
        -   **Domain Event**: *Captures the memory of something interesting which affects the domain*
        -   **Repository**: Only operates on aggregate roots and persists those objects. Changes only allowed through public methods on aggregate root. Not part of the domain model
        -   **Application services**: Like a controller: calling repository and public methods on domain object. Very thin layer.
        -   **Domain services**: When a business logic spans across several aggregates. Part of domain model.

# 📅 25.02.2022 How to bring the quiet on board?

-   Game \"Button\"
    -   \"Everyone speaks once before anyone speaks twice.\"
    -   In the beginning everyone has to raise their hands.
    -   Based on the talking stick tradition of the native americans
-   Everyone has to facilitate at some point
-   Do brainstorming not in anonymous mode

# 📅 25.02.2022 Alternative way of roles and reponsibility matrix (R.A.C.I.)

-   [source](https://en.wikipedia.org/wiki/Responsibility_assignment_matrix)
-   For each task/domain differentiate the following
    -   Responsible: Does the work (but can delegate if necessary)
    -   Accountable: Checks if work is done
    -   Consulted: Contributors, providing input
    -   Informed: Are kept up to date

# 📅 25.02.2022 Alternative way of Stackholder mapping Ask the follwing questions and then do a affinity mapping over power/interest quadrants

-   Who will be impacted by the project?
-   Who will be responsible or accountable for the project?
-   Who will have the decision authority on the project?
-   Who can support the project?
-   Who can obstruct the project?
-   Who has been involved in this type of project in the past?

# 📅 25.02.2022 Workshop formats I liked from Gamestorming book

-   **Brainwriting**: Each member writes stickes with idea and passes it to the next person who refines, appends an idea to that sticky
-   **Fishbowl**: One part of team has a discussion, the other listens and afterwards summarizes (done with inner, outer circle)
-   **Forced Analogy**: Come up with a random list of things and then find analogies to our problem: \"How is this problem similiar to XY?\"
-   **Low-Tech Social Network**: Graph on mural and people have to draw connections between them (hobbies etc.) - like \"Find 10 things you have in common\"
-   **Force-Field-Analysis**: In the middle \"Some change you want to achieve\" and both side \"Forces for change\" and \"Forces against change\" (from Lewin)
-   **SQUID**: Come up with questions, second round - ask questions. Repeat those steps, layer by layer

```{=html}
<p align="center"><img height=200 src="https://raw.githubusercontent.com/biocarl/img/master/squid.jpeg" /></p>
```
# 📅 25.02.2022 What questions to ask during a workshop (as facilitator) from Gamestorming

-   **Opening**
    -   \"How do you define the problem you are facing?\"
    -   \"What kinds of things do we want to explore?\"
    -   \"What are the biggest problem areas\"
-   **Navigating**
    -   \"Are we on track?\"
    -   \"Did I understand this correctly?\"
    -   \"Is this helping us to get where we want to go?\"
    -   \"Is this a useful discussion thread?\"
    -   \"Should we table this for now and put it on a list of things to talk about later?\"
-   **Examining**
    -   \"What is it made of?\"
    -   \"How does it work?\"
    -   \"Can you give me an example of that?\"
    -   \"Can you describe it in terms of real-life scenario?\"
-   **Experimenting**
    -   \"What are we missing?\"
    -   \"What if we are wrong?\"
-   **Closing**
    -   \"How can we prioritize those options?\"
    -   \"What is feasable?\"
    -   \"What can we do in the next two weeks?\"
    -   \"Who is going to do this?\"

# 📅 24.02.2022 How to secure your endpoints

-   Different options
    -   Lightweight Directory Access Protocol (LDAP) - [link of disadvantages](https://blog.lithnet.io/2018/03/the-ldap-authentication-anti-pattern.html)
        -   painfull due to credential rotation
    -   Credentials Flow - [link](https://auth0.com/docs/get-started/authentication-and-authorization-flow/client-credentials-flow)
    -   Mutual TLS - [link](https://www.cloudflare.com/learning/access-management/what-is-mutual-tls/)
        -   also ensures that traffic is encrypted

# 📅 22.02.2022 How to have engaging conversations in a team (workshop)

-   Add here also the campfire workshop (tell a story)
-   Two different types of identity
    -   local identity
    -   universal identity: \"I am human so nothing human is foreign to me\"
        -   We all have problematic families
        -   We\'ve all been disappointed
        -   We\'ve all been idiotic
        -   We\'ve all loved
        -   We\'ve all hated
        -   We all have dreams that we do not live
        -   We all have anxieties
        -   We all have ambitions
        -   We all have bodies that give us difficulties
-   You always have the choice to direct the conversation to deep talk or small talk
    -   Surface Self
        -   Where we go
        -   What we do
        -   Who we have seen
        -   What\'s been going on
    -   Deep Self
        -   What we fear
        -   What we love
        -   What we hope for
        -   What we regret
        -   What we\'re sad about
-   Releated workshop format: [Campfire](https://gamestorming.com/campfire/)
    -   Set the scene of sitting together at a fire
    -   Put on Mural the \"Wall of Word\" -\> people can use a word and tell a story and put that stick on the \"Story Thread\", which is growing snake-like during the workshop
    -   Before you \"put out the fire\", ask if there were any lessons learned, insights or feedback

# 📅 22.02.2022 Proxy environment variables in Unix

-   if you want to route traffic over a proxy you need to set those
-   `http_proxy`, `https_proxy`: Sets the proxy all traffic will go through
-   `no_proxy`: Comma-separated list of domain extensions the proxy should not be used for. For instance '.google.de', proxy will not be used for german google queries

# 📅 21.02.2022 Team: Agile routines I enjoy

-   Culture cafe
    -   present softskills, ways of working in a bi-weekly manner
    -   also encourage the client to contribute to it
    -   do series to build upon the sessions
    -   give small homework
-   Tech Huddle
    -   have a excel sheet where every can vote on the proposed topics
    -   let also other people ask for topics and someone else will present it
-   Book club
    -   vote for a book to read
    -   tbd
-   Health Check (e.g. in retros), more details elsewhere
-   Tech Health Check

# 📅 15.02.2022 A case against Spring profiles and beans depending on profiles **A case against profiles**

-   You should always externalize as much config as possible (see [12factor](https://12factor.net/config))
    -   **strict separation of config from code. Config varies substantially across deploys, code does not.**
    -   Reduces complexity

    -\> so even if using spring profiles they mainly should contain references to environment variables which makes different profiles obsolete
-   You also should not group configurations (may it be external or not) since this just increases complexity, each config parameters should stand for itself

**A case against profile dependent annotations**

-   You sometimes need different beans e.g. a different client logic depending in which environment e.g. also deploys for different tenants. To set this different behavior do not go for a `@Profile` because
    -   it is super confusing to know what is happening in which profile when looking at the code,epecially if you are using negations like `!test` -\> source: [Don't Use the @Profile Annotation in a Spring Boot App!](https://reflectoring.io/dont-use-spring-profile-annotation/)
    -   also makes test setup more complicated if certain beans require a certain profile to be active
    -   the more profiles you have adding up the more confusing it is to debug and understand which is overwritten by what
    -   **Solution**: Use a value environment in config file and then annotate the beans like so `@ConditionalOnProperty(name="service.mock", havingValue="true")`
-   technical learning: in `@ActiveProfiles` you do not specify several environments like in `@Profile`: `test,staging` but provide them as a array: `@ActiveProfiles({"test", "staging" })`

# 📅 11.02.2022 A nice way of checking the team health in the retro

```{=html}
<p align="center"><img height=400 src="https://raw.githubusercontent.com/biocarl/img/master/healthcheck.PNG" /></p>
```
# 📅 09.02.2022 What to do after a brainstorming session

-   Pre-define brainstorming outcome by setting a meaningful space beforehand
    -   Example: Give some grid and everyone has to arrange the stickies they put there in the appropriate corners e.g. High/Low Impact/Effort - Quadrants
    -   Other \"meaningful spaces\"

```{=html}
<p align="center"><img height=100 src="https://raw.githubusercontent.com/biocarl/img/master/20220224_215317.jpg" /></p>
```
```{=html}
<p align="center"><img height=100 src="https://raw.githubusercontent.com/biocarl/img/master/20220224_215351.jpg" /></p>
```
-   Everyone votes on the most important ideas (also vote with different emojis like ❤️‍/🔥)
    -   Similiar, idea of \"Forced Ranking\" (everyone needs to come up with their own ranking)
-   Talk through each items and allow people to join the discussion
-   Everyone presents their own sticky or do something else with it (e.g. invert it to the opposite)
-   Cluster according to certain criteria: Affinity mapping (JK Method)

# 📅 08.02.2022 Why you should never put PII data in url

-   A lot of components log url, man in the middle attacs and ajax calls from the browser (e.g. malicious browser extensions/browser history), user might not be aware what link they shared
-   **Solution**:
    -   \'Break\' with Rest and always do a POST and no GET (will be SSL encrypted)
    -   Put tokens etc in header

# 📅 03.02.2022 IntelliJ Set `pwd` in Shell

-   Just drag folder from tree view into shell and the `pwd` changes

# 📅 21.01.2022 Token generation via metadata server (GCP)

-   when running Cloud Run you usually have a deployer service account and a runner service account
-   In a Cloud Run Instance you can hit the metadata service endpoint which will do some Google magic to authenticate via the runner service account
-   Example for token generation: `http://metadata.google.internal/computeMetadata/v1/instance/service-accounts/default/token` (switch out default with the sa account you need)

# 📅 20.01.2022 Why VPC connector's are needed in GCP?

-   When using a Shared VPC
    -   Chunked in different subnets (IP ranges) is tied to one region (e.g. europe-west-1)
-   Serverless Services like Cloud Function and Cloud Run can't be deployed into a specific network (like a shared VPC) because they use their own google internal network
    -   That is why you need a VPC connector: routes incoming and outgoing go then through/to a shared vpc
    -   A VPC connector needs its own subnet (no other resources are allowed in there)
-   There is certain ingress and egress settings specifying which type of traffic is routed over the VPC and which not
    -   `all-traffic`: Sends all outbound traffic through the connector.
    -   `private-ranges-only`: Sends only traffic to internal addresses through the VPC connector.

# 📅 17.01.2022 - 19.01 Systemischer Coach - Ausbildung (Modul 1)

-   Methoden für Team
    -   World Cafe
        -   4 Kleingruppen + 4 Auserwählte
        -   Es gibt 4 Themen welche die Auserwählten durch die Kleingruppen tragen
        -   ursprünglich auf Tischdecke schreiben/ aber auch online möglich (breakout rooms für Kleingruppen während Auserwählte)

        ```{=html}
        <p align="center"><img height=200 src="https://raw.githubusercontent.com/biocarl/img/master/world-cafe.jpeg" /></p>
        ```
    -   Freies Spekulieren / Positives Hypothesieren
        -   Kleingruppen sprechen jeweils einer Person positive Eigenschafen zu
        -   Danach kann der Einzelne die Vermutungen richtigstellen
    -   Kreise/Felder auf Whiteboard aufzeichnen und jeder Einzelne ordnet sich dabei zu und man bespricht das

# 📅 14.01.2022 team: E.L.M.O. - The remedy against rabbitwholes

-   E.L.M.O. := \"Enough, Let's Move On\"
-   You would quietly raise your hand and after a critical mass of people raising their hand the people stuck in their discussion would stop and we laugh alltogether (according to theory)
-   For mobile: [meeting cards](https://mpetersen.github.io/meeting-cards/)

# 📅 11.01.2022 CIDR ranges and IPV4

-   How to calculate the range ([link](https://erikberg.com/notes/networks.html))
    -   you have a start IP (255 is max before next block is flipping)
    -   and a `/{range}` specifciation
    -   with that range you calculate the number of available IP\'s

    ```{=html}
    <p align="center"><img src="https://raw.githubusercontent.com/biocarl/img/master/cidr.PNG" /></p>
    ```
    -   the range you retrieve by incrementby that amount from the start IP
-   also watch this *<https://www.youtube.com/watch?v=MmA0-978fSk>*

# 📅 11.01.2022 Rules for ankifying business knowledge

-   No frameworks releated knowledge
-   No definitions of terms you will encounter frequently
-   Only ankify after some time (the longer the better)
-   Review on web, always pull changes on AnkiDroid after review

# 📅 11.01.2022 Conway\'s Law (Presentation by James Lewis)

-   Basic idea of microservices: Splitting in domains
-   The software architecture will mirror the communication of that organisation
-   Example: Open-Source
    -   is the most decoupled because everyone is very separate
    -   communication was asynchronous
-   Inverse Conway Maneuver ([link](https://www.thoughtworks.com/en-de/radar/techniques/inverse-conway-maneuver)) ✔️
    -   Adapt organisation structure according to your newly proposed software architecture
    -   Netflix: Teams which have to communicate with each other also physically next to each
    -   Organize product lines through whole stack/layers required

# 📅 11.01.2022 Versioning in multiple environments

-   Situation: When we publish a new version it can break other applications in the system (also potentially maintained by other teams). So by publishing we potentially block all environments, of all teams
-   Possible solutions
    -   For team owned environments you could make them resposible for pulling the newest version
    -   Push out regurarly to avoid not uptodate environments
    -   have a environment where the others are not dependent on to test first (with e2e etc.)
    -   use contract testing to avoid structural breaking changes
-   How to decide when to push out new versions to each environment?

# 📅 11.01.2022 Multitenancy

-   Definition: Sharing a single application for multiple tenants (different markets/environments) ✔️
    -   you just provide a tentant id and then request is handled accordingly by application
    -   often you have one database but different schema for the different tenants
    -   tentant groups get their own deployment
-   Two approaches
    -   Avoid Multitenancy: For each environment a different deployment
        -   no multitenancy problem
        -   take care only for a single environment
        -   very often legally required to have data seperated (country laws and Competition law)
        -   easier to debug (e.g. tracing just needs to be labelled with environment)
        -   fast lane for specific fixes (since you also have a separate pipeline) and do not have to wait for other deployments to go green
    -   One application serving multiple tentants (multitenancy) ✔️
        -   it is hard to find bottleneck in system for a specific tenant because e.g. backpressure might comes from a different tenant where the same application is also responsible for
            -   Issue: Separation of concerns is not equivalent to the separation of ressources
        -   all tests for other tentants have to green before deploying
        -   takes longer to do migrations (you have to do this for all tentants)
    -   You can do multitenancy on several levels

    ```{=html}
    <p align="center"><img src="https://raw.githubusercontent.com/biocarl/img/9eb6460880f5e3ec606d7128be0db658f1ddccab/The-multi-tenancy-continuum.png" /></p>
    ```

# 📅 11.01.2022 How to embed images in org files (rendered on Github)

-   Upload to img repo and then open image in new tab and ue the githubusercontent url

``` {.bash}
#+html: <p align="center"><img src="https://raw.githubusercontent.com/biocarl/img/34edba9d7e71c0887534bf0310ba0c137f59afbc/gap_map.png" /></p>
```

# 📅 10.01.2022 InfoSec: How to tackle dependency drift?

-   dependency drift :=dependencies coming out of age slowly
-   if static version numbers
    -   how to ensure that people go over them and update? How to decide?
-   if automatic dependcy increment (like latest)
    -   there is no instance checking those patches if they introduce a bad actor for example
-   there is managed and recommended lists of version (see here bom files)
-   when having semantic versioning of dependencies you can for instance do automatic increasing of versions on patch versions but manual increment on minor or major versions
-   incrementing major or minor versions is usually also needing a new feature set which does not necessary increase security and requires expertise and testing for verifying that no breakin changes occur

# 📅 10.01.2022 InfoSec: For what to sign a Data processing Agreement (DPA)?

-   DPA: Data processing Agreements
    -   even potentially pairing with someone who shares PII data via screensharing has to be covered
    -   also as external consultancy this is required for the client because we can often easily elevate access and therefore access prod data (think of audit logs etc.)

# 📅 10.01.2022 workshop: How to run a futurespective/ Learnings from minion futurespective

-   Exercises
    -   Hopes and Concerns [- link](https://www.funretrospectives.com/hopes-and-concerns/)
        -   Try to focus on the positive
        -   afterwards encourage the team to do something so their hopes come true (by this work really becomes fun again)
    -   That Guy and This Guy [- link](https://www.funretrospectives.com/that-guy-this-guy/)
        -   You called it \"team culture\"
        -   Think of people/experiences from past/current projects and how they guided you
        -   \"So if you are seeing here some behavior which can can identify with don\'t take it personal. Probably a lot of people show this kind of behavior and/or the remark might result from a totally different context/project\"
        -   Alteration:
            -   First each person brainstorms 5 mins the behaviour they dislike
            -   then you say you can\'t bear all that negativity and they are responsible to invert and propose better behavior
            -   for each sticky they have to put in a positive behaviour alternative, thereby it is good to encourage that not only the negation of a behavior is possible: e.g. comes to late -\> comes on time -\> comes even 5 mins earlier to socialize
            -   Each person has to present their positive and negative behaviour
            -   While the others have the option to reflect on their behaviour
                -   what bad behaviours you catch yourself doing sometimes?
                -   which positive behaviours would you practice more?

# 📅 10.01.2022 Team: High-Performing Teams

-   Warmup-Question: Tell us a story: What was the best team you were ever part of?
-   Five Dysfunctions of a Team (Book) [link](https://www.youtube.com/watch?v=GCxct4CR-To)

```{=html}
<p align="center"><img src="https://raw.githubusercontent.com/biocarl/img/master/dysfunction.jpeg" width="500" /></p>
```
\#+END~SRC~

-   **Absence of Trust**: Without trust you do not have the base to go into conflict
    -   Action: Do the first step and share challenges, fears and limitations
-   **Absence of Conflict**: This is not only ok but necessary in a team. It is just a way to persue truth
    -   Action: Cultivate safe environment for diverse opinions, ask questions
-   **Absence of Commitment**: Without conflict you do not commit, you do not care about the decisions and just go along
    -   Action: Make outcomes specific and crisp (also DoD - Definition of Done)
-   **Avoidance of Accountability**: Without commitment we won\'t hold each other accountable. If people are commited they also will have the courage to confront each other
    -   Action: Confront difficult issues
-   **Inattention to Results**: Not paying attention to results, at least not to the collective results. Everyone is just caring about themselves
    -   Action: Focus on collective results

# 📅 06.01.2022 Spring: Declare a object instance as a bean

``` {.java}
@Configuration
public class SomeConfig {
    @Bean
    public ObjectA objectA(){
        return new ObjectA();
    }
}
```

# 📅 06.01.2022 Spring: Learnings about Spring Dependencies

-   You can use the [Dependency Management Plugin](https://docs.spring.io/dependency-management-plugin/docs/current/reference/html/)
-   or import bom files with gradle 5 [link](https://docs.gradle.org/5.0/userguide/managing_transitive_dependencies.html#sec:bom_import)
-   purpose is here explained - [link](https://blog.mrhaki.com/2019/04/gradle-goodness-use-bill-of-materials.html)
-   if bom has some old dependency recommendations (not updated), you can overwrite with this

``` {.groovy}
dependencyManagement {
    imports {
        mavenBom 'urltobom:version'
    }
    dependencies {
        dependency 'url:artifact:version'
    }
}
```

# 📅 06.01.2022 QA: Learnings about pact and contract testing

-   usually you write consumer tests in form of Unit tests and from those a pact file (contract) is generated

-   that pact file can be shared via a pact broker with the provider where that file is used to generate provider tests

-   you only want to test syntax and semantics, you do not want to test functionality [source](https://docs.pact.io/consumer/contract_tests_not_functional_tests)

    -   that means: A contract test does not check for side effects! (e.g. db entry created etc.)
    -   what about validation and error reponses?
        -   it is good to cover sad path\'s to make sure that consumers know\'s how provider behaves in such cases

        -   BUT do not test all the different validations

        -   otherwise we create unnecessarily tight contract: e.g. if provider chooses to increase the char limit for a username that would unnecessarily break the contract for the consumer

        -   \"Write scenarios about how the validation fails, not why the validation fails\"

        -   Concrete example: Test one validation and do not care about specific failure but format

            ``` {.bash}
            Response is 400 Bad Request
            Response body is { "error": "<any string>" }
            ```

-   for pact file specification - [link](https://github.com/pact-foundation/pact-specification)

-   you can run provider tests either via a deployed instance / containerized local instance or do this via the unit test level where you call e.g. controller methods with the pact file defined input and convert this to JSON and compare this with the pact file provided output

-   when running e2e tests or pact tests you always need to take care of certain pre-conditions/states/setting up data, this can be quite complex

    -   often best to do this on a unit test level: you can mock/stub easily and do not need a populated database
    -   when using a real instance you should think of snapshoting certain db states for quicker state setups
    -   pact does not recommend to run pact tests against a public API because you can only setup the data via that API, making it slow and cubersome (also to reset)

# 📅 04.01.2022 Agile: Laws

-   **Conway's Law**
    -   \"Any organization that designs a system (defined broadly) will produce a design whose structure is a copy of the organization\'s communication structure\"
    -   Isomorphism between org communication structure and software design
    -   Examples
        -   if frontend and backend code is completely separate because there is also different teams
        -   if there is no product teams but feature teams this does not support the idea of microservices and ownership
        -   if there is a team for each country resulting in different codebase and approaches
-   **Hackmans' Law** ([source](https://blog.nuclino.com/two-pizza-teams-the-science-behind-jeff-bezos-rule))
    -   \"The larger a group, the more process problems members encounter in carrying out their collective work. \[...\] It's managing the links between members that gets teams into trouble.\"
    -   Also called coordination costs
    -   Ideal team size: Jeff Besos called this the Two-Pizza rule (meal for an ideal team)
    -   Number of links between members grow exponentially with growing team size
    -   That is the reason why introducing roles and norms is even more important (differentiation vs cohesion)
-   **Brooks' Law**
    -   \"Adding human-power to a late software project just makes it later.\"
    -   Because of Hackmans\' Law
    -   but also due to time to onboard and fact that certain tasks can\'t be devided:
        -   \"Nine women can't make a baby in one month.\" (see also [disjunctive tasks](https://en.wikipedia.org/wiki/Steiner%27s_Taxonomy_of_Tasks#Disjunctive))
-   Goodharts' Law
    -   \"When a measure becomes a target, it ceases to be a good measure.\"
    -   For example when university rankings were introduced, univesities started to focus only on rankings
    -   Also related to game theory: \"Tell me how you measure me and I will tell you how I will behave.\" (Eli Goldratt)
    -   also related: perversive incentive
-   Larmans' Law
-   Parkinsons' Law

# 📅 04.01.2022 Java: slf4j vs log4j vs logback

-   slf4j is a specficiation which logback is implementing
-   Log4J is the predecessor of logback

# 📅 04.01.2022 Weblogic 101

-   Application server for Java EE applications

# 📅 04.01.2022 Java EE 101

-   With Java EE you can easily scale because you can distribute the EJB\'s to different servers
-   The EJB (Enterprise Java Bean)
    -   Java EJB vs Spring Beans
        -   Java EJB is only a specification and implemented by application server e.g. Weblogic
        -   Spring Bean is already a implementation
    -   `@Remote`: The bean implementation can run on a different server, in different jvm (vs `@Local`)
-   `@Interceptors`: Implementing cross-cutting concerns like logging, auditing. Hooks into lifecycle and executes custom code like log when EJB is destroyed

# 📅 04.01.2022 Workshop: How to design workshops?

-   Warmup-Question: What is the first thing that comes up when you hear about that topic?
-   Present in the beginning what the outcomes of the workshop are
-   Nice last slide or mural unit
    -   GIVE US FEEDBACK.
    -   1 STICKY TO STRENGTHEN CONFIDENCE
    -   1 STICKY TO IMPROVE EFFECTIVENESS
-   Use svg generators to get nice backgrounds/structure of canvas
    -   blobs ([blobmaker](https://www.blobmaker.app/)) and put transparent brushes structure on forms
    -   or this [svg generator](https://app.haikei.app/)
-   When giving homework, usually if they are given to each person without a way of controlling the outcomes it is sometimes good to give them to a pair (so the likelyhood increases that one follows up) Example: \"Homework: Give a feedback to someone\" -\> Assign pairs to do this

# 📅 18.12.2021 Team: Thinking about the team

-   Good list for online games - [link](https://www.flcc.edu/pdf/studentlife/OnlineBoardGames.pdf)
-   General ideas of LEAN
    -   Central values
        -   Focus on value generation
        -   Quick feedback cycles
        -   Self-Organizing teams
    -   Subsets are Kanban, Scrum

# 📅 18.12.2021 Anti-Corruption-Layer

-   [source](https://dev.to/asarnaout/the-anti-corruption-layer-pattern-pcd)
-   If you want to integrate with a legacy system, but this legacy system does not fit with your newly defined domain model
    -   e.g. old conventions you want to do differently (unit from inch to meter)
    -   e.g. exposes several interfaces which from your viewpoint should be one (e.g. prepare shipping, optimize shipping and execute shipping -\> do shipping)
-   by introducing a layer of abstraction which translates, adapts your client call to the legacy system you avoid that legacy assumtion to do not corrupt your new system while not having to touch the legacy system
-   a anti-corruption-layer can also be bi-directional (when legacy system also has to call back to new system)
-   alternatives to an anti-corruption layer are
    -   Conform to legacy system (use same model assumptions etc.)
    -   Replace legacy system
    -   Do not integrate with legacy system
    -   EAI system (enterprise application integration)

# 📅 17.12.2021 Git amend change in commit which was not the last one

-   Step1: `_git rebase --interactive 'bbc643cd^'_` /hash of the commit which was before the desired change (note also the carret)
-   Step2: Change from pick to edit for the commit you want to change
-   Step3: Add to staging and do `git commit --amend --no-edit`
-   Step4: Do the actual change and then do `git rebase --continue`

# 📅 16.12.2021 Which team should take care of service x?

-   Responsiblity: Who introduces the service and therefore should own it?

vs

-   Dependency: Which team can afford to be dependent on the other team? What happens if service x does down and other team is not available?

# 📅 15.12.2021 Terms

-   WADL: Web application description language: XML description of a REST service (e.g. like swagger in yaml/json)
-   WSDL: WADL equilvalent for SOAP service
-   `.xsd`: A schema for an `.xml` file

# 📅 15.12.2021 Deactivate IntelliJ Bell Sound for vim emulation

-   `set visualbell`
-   `set noerrorbells`

# 📅 14.12.2021 Unix routing and networking

-   Check if a certain port is open
    -   `telnet ip port`
-   Check if a hostname resolves to a certain IP
    -   `host address_name`
-   If you want to route a domain name to a IP
    -   edit `/etc/hosts`
    -   Format: IP -\> adress~tobemapped~
-   If you want to map from one IP to another IP (`127.0.0.1`)
    -   `iptables -t nat -A OUTPUT -p all -d  192.168.101.101 -j DNAT --to-destination 127.0.0.1`

# 📅 10.12.2021 Gradle: Lazy and eager configuration/creation of tasks

-   Usually all tasks are configured right from scratch (configuration phase)
-   this can lead to issues if you only want to configure certain things when you actually execute a task
-   for lazily configuration have a look at [task configuration avoidance](https://docs.gradle.org/current/userguide/task_configuration_avoidance.html)
-   `create` ist eagier und `register` lazy task creation/configuration
-   for an existing task you want to configure (only when executed)
    -   `tasks.named('bootRunLocal').configure{}`

# 📅 08.12.2021 Learnings about liquibase

-   `relativeToChangelogFile`: Allows you to reference other changeset relative to the parent changeset and not from classpath (needed e.g. when applying liquibase migrations from different contexts local and test)
-   a changelog file allows you to group changes based on domain/table etc.
-   you can either execute migrations through Spring or in a separate Gradle task
-   Liquibase allows for specifying contexts so that only specific changesets are executed in a certain environment
-   You can also specify several activities (set of configurations) which can run one after another (see runList)

# 📅 08.12.2021 Curl: Simple GET with basic auth header

-   `curl -v  -H "Authorization: Basic (base64 username:pw)"`

# 📅 07.12.2021 Bash: Reverse Search in Unix

-   Search: `CRTL` + `R`
-   Cycle through results: `CRTL` + `R`

# 📅 06.12.2021 Postgres: Grants in postgres

-   `GRANTDELETE ON ALL TABLES IN SCHEMA PUBLIC TO root;`
    -   Grants privileges only to existing objects
-   `ALTER DEFAULT PRIVILEGES IN SCHEMA PUBLIC GRANT DELETE ON TABLES TO root;`
    -   Grants privileges only to future created objects

# 📅 06.12.2021 Api: Two ways of Api-Design

-   Two common approaches (see also REST vs RPC style - [link](https://blog.jscrambler.com/rpc-style-vs-rest-web-apis))
    -   REST ressource: `/accounts`
    -   Reified resources: `/create_account`
-   You can also combine the two
    -   `/create_account (for posting)`
    -   `/accounts (GET)`

# 📅 25.11.2021 InfoSec: Learnings about security

-   General rules
-   Build with security in mind right from the start
-   Build several layers of security in case one fails
-   Principle of least privilege
-   Prefer allow-lists over denylists
-   Do not reinvent the wheel
-   Threat Modelling
-   always involves product people and delivery team (and SME of InfoSec) -\> Shared understanding
-   iterative process (can also be done when new features are created)
-   Business Thread Modelling (High-Level approach)
-   artifact is a priotized list of threads -\> after that we have to ensure that our application is designed accordingly (see Application Threat Modelling)
-   As preparation: CIA triad, buiness understanding, Identify actors
-   CIA triad
    -   Confidentiality: Only authorized access of data
    -   Integrity: Data should be tampered/manipulated
    -   Availability: No downtime (e.g. hospitals)
-   Identifying actors (entities like services or people)
    -   best done by looking the workflows or already during inception
-   Identify assets (what can be compromised/stolen)?
-   How to manage threat?
    -   Risk register: Threat, Impact, Probablity, Severity (Im\*Pr), Mitigation
    -   Magic quadrant: Probablity and Impact -\> When it comes to prio, start with high probablity and impact
-   Application Threat Modelling
-   based on identified threat list in step one: what would the attacker do to achieve this threat? How does the application enable/prevent this?
-   Types of attacks (STRIDE)
    -   Spoofing (pretend to be someone else): Can an attacker gain access using a false identity?
        -   Example: [Sony Picture Hack](https://en.wikipedia.org/wiki/Sony_Pictures_hack) started with fake Apple Id Mail
    -   Tampering (e.g. inject script): Can an attacker modify data as it flows through the application?
        -   Example: [Samy worm](https://en.wikipedia.org/wiki/Samy_(computer_worm))
    -   Repudiation (e.g. remove traces of illegal actions): If an attacker denies doing something, can we prove he did it?
        -   Example: [Lotterie Incident](https://darknetdiaries.com/episode/101/), changing db before payout
        -   Example: Access on celeb profiles are tracked in federal agency for work
    -   Information Disclosure (e.g. stacktrace in the UI): Can an attacker gain access to private or potentially injurious data?
        -   Example: hacked binance account on crypto, you were able to see if a certain mobile number was used for account. First step for proceeding with SIM swap
        -   Example: Exposing stacktrace on UI
    -   Denial of Service Attack (DoS): Can an attacker crash or reduce the availability of the system?
        -   Example: Anonymous attacking police stations, governments, scientology or even childrens hospitals
        -   Example: Self-Made Dos, no circuit breakers in a distributed system
    -   Elevation of Privilege: Can an attacker assume the identity of a priveliged user?
        -   Example: Used in almost every major hack, using not patched vulnerabilities to e.g. become super using on host OS
-   How to manage threat?
    -   Data Flow Model: How does data change and what are the \'trust boundaries\'?
        -   trust boundary := one defined region where services trust each other (e.g. webbrowser is not in the same boundary as the backend). What is under your control - what are external entities
        -   each trust boundary is exposing a certain attack surface. Apply STRIDE here
        -   In a last step, think of risk mitigations
    -   Play [card game by owasp](https://owasp.org/www-project-cornucopia/)
    -   Attack Tree
        -   get into the role of an attacker
        -   always ask why the attacker is doing something, thus opening potential other ways of achieving this
        -   do not focus on the concrete techniques which might be deployed but more about the goals (and why)
        -   group those approaches in parent goals and then try to enrich the constructed tree (adding child or sibling)
        -   in a final step you should think where in the tree you can apply possible mitigations (start from bottom up). What is in your controll and what not? (Principle: Defense in depth - defend in multiple layers)

# 📅 25.11.2021 Pattern: Dealing with transactions in the world of microservices

-   Two-Phased Commits (2PC)
-   not acid (usually only eventually consistent, each microservice locking, executing)
-   distributed locking systen
-   only use for very short lived operations (introduces latency, because resources are locked)
-   Process
    1.  Voting Phase: Ask each are you able to complete the work? If so, lock rows and return ok to coordinator node
    2.  Commit Phase: Change will be made persitent (no atomicty, only eventual consistency)
-   Best Approach: Keep transactional logic in one microservice
-   Saga-Pattern
-   Idea: Each microservice has local transactions which trigger local transactions in other microservices (e.g. through queuing system)
-   If one local transaction fails some fixing transactions are back propagated (for cleanup or mitigation)
-   Type: Choreography
    -   Each microservice is keeping tracking of its state and notifies other dependent transactions
    -   Risk: Difficult to see relationships between microservices and risk of cyclic dependency
-   Type: Orchestration
    -   Central actor which is keeping track of the states (e.g. listening to a queue) and notifying which microservices have to perform which local transaction / fixing transaction
    -   Risk: Additional point of failure, requires new microservice to maintain

# 📅 24.11.2021 Git: When you clone a repo you do not want to push back to

-   `git remote -v`: List remotes if a repo
-   `git remote rm origin`: Remove remote of a repo

# 📅 24.11.2021 Database modelling

-   Logical/Relational (relationships, entities) vs. Physical (how it actually looks like with datatypes) model
-   best picks for postgres: pgModeler, Moon Modeller

# 📅 24.11.2021 UML: Tool for modelling sequence diagrams

-   PlantUml (also with IntelliJ Plugin and can be embedded in Confluence)

``` {.bash}
@startuml
Alice -> Bob: Pays money
Bob --> Alice: Gives ice cream
@enduml
```

# 📅 11.11.2021 IntelliJ: Make Maven work in IntelliJ

-   Look for crossed out POM, remove from ignored files list under gradle settings
-   In Maven Window, find root project and do clean/install
-   Right click on project folder maven\>generate sources helped to make annotations etc. working

# 📅 09.11.2021 Team: Reflections and learnings about **feedback**

-   **Feedback triggers**: When is it difficult to recieve feedback? (the Book \'Thanks for the Feedback\')
    -   Truth trigger: We feel that feedback is wrong, incomplete
    -   Relationship trigger: We feel person giving it is not trustworthy, competent -\> attention shifts to the person, away from the feedback
    -   Identity trigger: Feedback about parts we consider super important to our identity
-   **Types of feedback**
    -   Evaluation: Where you stand (assessment, ranking etc.) -\> Align expectations
    -   Appreciation: Relationship/Human Goals - \'we all have a common goal, you are helping us with that\' -\> Makes us feel good
    -   Coaching: Help someone learn, grow and change, ressource focused, concrete -\> Gives us sense of purpose
-   **How feedback is created**
    -   There is always a gap between what we think we present and what other people see

```{=html}
<p align="center"><img src="https://raw.githubusercontent.com/biocarl/img/34edba9d7e71c0887534bf0310ba0c137f59afbc/gap_map.png" width=400 /></p>
```
-   In the spirit of constructivism you do not understand
    -   their system
        -   their intention
        -   how they view things
    -   nor do you understand your own
        -   interpretations
        -   completeness of your data
-   Therefore, when you give feedback try to focus about the behavior and understand their intention first

```{=html}
<!-- -->
```
-   "He said, when you're screwing up and nobody's saying anything to you anymore, that means they gave up. And that's a lesson that stuck with me my whole life. Is that when you see yourself doing something badly and nobody's bothering to tell you anymore, that's a very bad place to be. Your critics are your ones telling you they still love you and care." - Randy Pausch
-   Good exercise: Each person draws a picture and you swap with your partner and exchange feedback
    -   How did you feel as a giver? Was it easy? Did you use any specific techniques? Was your feedback incorporated in the drawing? Was your feedback listened to? Did you get the result you expected?\"
    -   How did you feel as a reciever?
    -   Learning: Some people really do not like drawing, think of different artefact or give them more preperation time to do the drawing (give 1 day to prepare)
-   there is also a concept of **feedforward**
    -   you yourself ask a person about something you want to have feedback on, usually before you expose that behavior you want to get evaulated. A good way of lower the barrier of getting into feedback since you select the person (comes down to trust) and the topic you want to have feedback on
    -   there is also a very nice form of feedforward

    ```{=html}
    <p align="center"><img height=400 src="https://raw.githubusercontent.com/biocarl/img/master/feedforward.jpeg" /></p>
    ```
-   Benefits of recieving feedback
    -   Acknowledgement: Often we see something which our teammate did well but we do not take the time to also communicate this to him. It is actually pretty nice if get to hear what you did well, maybe you want to get even better
    -   Sense of purpose: If you getting a feedback more often this is a perfect indicator that something might correspond to reality and I goes there is no one who does not like to be a person people like to work with -\> Motivation
    -   Identify blind spots
    -   Almost everyone loves receiving feedback, but hates giving it (especially the negative feedback, better to call redirecting feedback)
-   Joy of Giving feedback
    -   Reciprocity: First of all, a easy one - more from a game theory perspective: You like to have good feedback, so what you expect from others you should also deliver
    -   Feedback as a gift: We all like to grow and to get appreciated - a well placed feedback, leading to more understanding makes them super happy
    -   Opportunity to evoke change: If you have some small irritations you never reflected on but then bring them into contact -\> thus making you more productive
-   Instead of framing feedback as postive and negative, frame it as +/δ (for change)

# 📅 05.11.2021 workshop: Ideas to retro

-   Energizer: Find 10 common things as a team
-   Brainstorming: Find Good, Improve, Adventure Time (crazy, audacious ideas - do this at this end)
-   also celebrate good things (let people present the clusters)
-   Hide some small reference on the Mural/Jam-Board people have to find (like Wimmelbild)

# 📅 21.10.2021 Terms

-   Anti-Corruption-Layer Pattern: Create a layer to protect your domain: e.g. Player domain (in the facade it interprets what a Player can mean in other domains e.g. football or baseball player behavior)

# 📅 21.10.2021 microservice: Microservices 101

-   Advantages
    -   autonomous teams
    -   diverse set of technologies
    -   independent life cycle
    -   easy to understand a single microservice
    -   easy to compose services
-   Migrate from monolith to microservices
    -   tips for starters: first try decoupling a simple/decoupled function of a monolith
    -   Avoid coupling back to the monolith
    -   deploy early and then release
-   Change patterns
    -   Strangler Fig Pattern: Extract functionality from the egde of a system to a microservice Steps
        -   1.  Put proxy layer in front, intercept inbound call (does not work if logic lives deep inside the monlith)

        -   1.  Reroute traffic to new implementation

        -   1.  Delete old implementation

        Details
        -   use this if you must not touch the monolith\'s code
        -   when intercepting call you can do this via proxy or redirect, can even change the protocoll e.g. soap -\> rest
        -   even though not preferred you can still call back to monolith if this allows for small extraction
        -   you can also intercept response/request and just add something before/after it is processed by upstream/downstream services, called **decorating collaborator**
            -   example a new field is added in the response which seperately calcukated based on other fields in the response
            -   with this you also do not need to touch the orginal monolith
    -   Branch by abstraction: Create abstraction over functionality you want to use and then easly switch over between old (code living in monolith) and new implementation (a http call to the microservice)
    -   Parallel Run: Can be used in combination with the ones above: calling both implementations at the same time. Usually you have a validation to check if both implemenations work in the same way
    -   Change Data Capture Pattern: Listen to database changes with microservices to add additional functionality

# 📅 21.10.2021 Networking 101

-   **VPC**: Virtual private Cloud - Pool of shared ressources
    -   in Google this is a global construct
    -   usually three implicit firewall rules
        -   block all incoming traffic
        -   allow all outcoming traffic
        -   allow all internal traffic
-   **Subnetwork** : Is a portion of the orginal IP range defined in a specific region
-   **Shared VPC** : A VPC accros projects on a org level
-   **NAT** : Network Address Translation - Allow multiple private IP adresses/actors to access internet through one or more public ip adresses, also used for port mapping
    -   if local device (with local IP in network) wants to access internet it would send package to NAT
    -   that NAT then stores request with local IP and target IP into NAT table and switches out local IP with public IP of router
    -   once reponse returns, NAT looks in the NAT table and looks up the local device it needs to forward the package to
    -   each entry in NAT table has a timestamp which timeouts to close the port for target IP after some time
    -   this is usually referred as SNAT, because connection established from source
    -   if you want to establish a connection from outside it is called DNAT (from destination), also called Port-Forwarding
-   **Gateway** : in context of VPC: Talk to other VPC, to internet or to on-premise O
-   **Proxy** : a intermediary service which acts on your behalf
    -   if traffic between your services and proxy layer is encrypted: VPN
    -   different types catageorized by functionality
        -   open proxy / forwarding proxy server
            -   *this is protecting/hiding the client (sending side)*
            -   If hiding client IP, often called Anonymous proxy, otherwise transparent proxy (by setting like `X-Forwarded-For`)
                -   **but** transparent proxy has another meaning:
                -   in the sense of inline proxy, forced proxy
                -   proxy just intercepts the traffic and nothing has to be configured from the client side (done by surrounding infra)
                -   a famous example is also a CDN
            -   different use cases
                -   **caching proxy**: reduce data transfer (in internal network), caching requests
                -   **filtering proxy**: typical org policies to not access social networks etc.
        -   reverse proxy
            -   *this is protecting/hiding the server (recieving side)*
            -   usually public exposed layer to the internet
            -   in case of cloud: forwards request from internet to server located in VPC
            -   different use cases
                -   for compression (see also spoon feeding, serving content to client directly)
                -   **load balancer** is a special case, not about identity but distributingload to several identical servers
                -   **api gateway** is a sophisticated load balancer: API can be configured dynamically
                    -   -   security: often has denylist, accepting only a certain amount of requests from one client etc.

                    -   -   scalability: backend can change, wheres public ip stays the same

                    -   -   performance: e.g. caching and compression
-   **Routes**: How to send traffic from one instance to a destination (in VPC or internet etc.)
    -   a route consists of a single destination prefix in CIDR format and a single next hop
    -   routing table stores those routes (sometimes also with distance etc.)

# 📅 19.10.2021 Unix: Insert clipboard into file without editor

-   `cat > out.txt`, will open input mode
-   insert clipboard and then `CRTL + C`

# 📅 07.10.2021 Data Engineering

-   **Shuffling**: Usually data is distributed, meaning data is in different kinds of places. To do an operation like GroupBy they have to reside in on place. The process of moving/centralizing data is called shuffling. ([source](https://www.coursera.org/lecture/scala-spark-big-data/shuffling-what-it-is-and-why-its-important-bT1YR))

# 📅 05.10.2021 How problems are solved (debug,fix,issues)

-   docker compose: run services seperately and then try things out from the container itself
    -   `docker-compose up SERVICE_A`
    -   `docker-compose run --entrypoint=bash SERVICE_B`
-   docker-compose: Container was crashing immediately.
    -   substituting entrypoint with bash and discovered that this is a line ending issue
-   GCP: Look at audited ressources logs for more specific failure analysis
-   docker: Append cat command after java entrypoint in dockerfile to print out some error log file
-   Look at the classes when reading a stack trace!
-   Paint a diagram
-   Use debugger, jump to exception
-   Invest much time in reproducing issue locally first

# 📅 05.10.2021 Docker Compose: Commands

-   if you want to prune volumes with docker-compose: `docker-compose down --volumes`
-   if you want to build with docker-compose: `docker-compose up --build`
-   if you want to copy file into container: `docker compose cp fileInHost serviceName:targetFile`

# 📅 05.10.2021 Docker: Commands

-   `docker build --tag my_new_image .` : build new image locally, run this in the same folder where Dockerfile is located
-   `docker run -it <image> /bin/bashc` : create container and shell in
-   `docker run -p <outer>:<inner> <tag>`: With port mapping
-   `docker-compose exec service-name-in-docker-compose sh`: shell into existing container via service name

# 📅 01.10.2021 Postgres: Commands

-   `\list` or `\l`: list all databases
-   `\c <db name>`: connect to a certain database
-   `\dt`: list all tables in the current database using your `search_path`
-   `\dt *.`: list all tables in the current database regardless your `search_path`
-   `SET search_path TO myschema,public;`: Set schema for session

# 📅 01.10.2021 Unix: Fork commands and put tasks into foreground again

-   fork command with `&` and see background tasks with `jobs` and get task into foreground with `fg`

# 📅 01.10.2021 Windows: Avoid that windows goes into hibernate/sleep mode

``` {.powershell}
param($minutes = 60)
$myshell = New-Object -com "Wscript.Shell"

for ($i = 0; $i -lt $minutes; $i++) {
  Start-Sleep -Seconds 60
  $myshell.sendkeys(".")
}
```

# 📅 01.10.2021 Docker: Prune volumes

-   sometimes docker [caches ressources even across projects](https://github.com/pydanny/cookiecutter-django/issues/1678), if there is some wired behavior you should prune the volumes
-   `docker system prune -a --volumes --force` (don\'t do this in prod)

# 📅 22.09.2021 Terraform: Basics

-   if resource is not updated you can `terraform taint` the ressource (get address by `terraform state list`)
-   sometimes you get a state lock - to resolve this do `terraform force-unlock ID`
-   if you want to track a resource via terraform which was initially not provisioned by terraform do `terraform import resource_type.identifier ID`.
    -   you have to add a resource definition with name ID, why is applied right after the import command
    -   resource~type~.identifier could be for example: google~pubsubtopic~.projects/{{project}}/topics/{{name}}
-   `moved {}` block helps you to rename a ressource (or move to a module) without recreating the resource

# 📅 17.09.2021 Fun: gitmoji

-   there is some conventions to make commit messages mor pretty with emojis - [link](https://gitmoji.dev/)

# 📅 16.09.2021 Database: Terms

-   Surrogate key, almost like a primary key

# 📅 14.09.2021 Windows: Lock/Unlock F1-12 keys

-   Press ESC + Fn to toggle

# 📅 10.09.2021 Consulting: Terms

-   SME: Subject matter experts

# 📅 09.09.2021 Terms

-   lift & shift: Move existing on premise applications to the cloud without modifying them
-   Roll Back the Database or Fix Forward?
    -   Rolling back is very time-consuming and complicated
    -   Fix forward is a lot quicker
    -   always ensure that migrationns

# 📅 08.09.2021 Python: Quick start with isolated environment

-   python3 -m venv venv && source venv/bin/activate
-   pip install -r requirements.txt
-   Use debugger: import pdb; pdb.set~trace~()

# 📅 08.09.2021 pact: How to do contract testing?

-   [source](https://www.youtube.com/watch?v=U05q0zJsKsU&list=PLwy9Bnco-IpfZ72VQ7hce8GicVZs7nm0i&index=1)
-   In a microservice context integration is hard
    -   all have to be in the same environment
    -   slow
    -   hard to parallelize
    -   hard to debug (in which service was it failing?)
-   One solution: Spec-First design
    -   e.g. with OpenApi spec
    -   Good communication tool
    -   Problem: When updating the spec to v2 - a lot of consumers are breaking now
-   Better solution: Consumer-driven contracts

# 📅 07.09.2021 Pattern: Outbox pattern

-   outbox pattern := Create events table which is then published as events e.g. with CDC
    -   also called Transactional outbox pattern
    -   Problem description ([source](https://microservices.io/patterns/data/transactional-outbox.html))
        -   Microservices do not exist in isolation and have to propagate own data changes to other services
        -   How do you make sure that you commit changes in application **and** propagate the changes? In theory the first part could go through but the seconds fails, then you have inconsistent state accross the system
    -   Why not using CDC aka just streaming each change without staging table, directly?
        -   advantage: do not bind consumer of the event on the implementation of the datatable, you have no controll what the event looks like
    -   Problem about a syncronous approach (just calling dependent services via Rest for instance):
        -   a lot of consumers to take care off
        -   service can\'t function without the other services (latency is determined by slowest dependent)

# 📅 07.09.2021 Learnings

-   Reconciliations run: Check if two data sources are in sync
-   staging tables: containing business data, prepared for being loaded by the application (cleaning/modification beforehand), only temporary
-   **change data capture (CDC)**: A set of design patterns to capture changes in a data source
    -   lacking re-playability: new service can\'t consumer old changes

    ```{=html}
    <!-- -->
    ```
    -   including
        -   timestamps
        -   version numbers
        -   log scanners which emit detected transactions as a change event

# 📅 30.08.2021 GCP CLI

-   Showing current running builds: `gcloud builds list --ongoing`

# 📅 30.08.2021 Monitoring

-   Micrometer: metrics collection facade, like SLF4J but for metrics
-   Spring Boot Actuator: provides common metrics and autoconfiguration
-   REST vs RPC?

# 📅 25.08.2021 Contract-First vs Code-First

-   Contract-First
    -   Autogenerate DTO from existing Open-Api definition
    -   what happens if a new swagger definition breaks existing contract?
        -   you use minor/major versions to avoid to automatically pull (since a new DTO definition can break the code
    -   (+) Have a final version which allows others to talk about it (perfect for non-technical people)
    -   (-) for having contract-first you can do a contract-testing and should not rely on Swagger/Open-API.
    -   (-) you need to update open-api definition in repositoriy manually if you change behavior in code
        -   but still you could automate publishing of code-first generated contract
-   Code-First
    -   Generate Open-Api defintion from code
    -   (+) The agile way. Specifying it is part of the processes and not some final version (as in contract-first), less work

# 📅 19.08.2021 Under the Covers of Spring Boot

-   [source](https://www.youtube.com/watch?v=jDchAEHIht0)
-   Two phases of scanning
    -   1.  User configuration (`@Component`, `@Configuration`, `@Controller` etc.) - enable by `@ComponentScan`

    -   1.  Auto configuration - enable by `@EnableAutoConfiguration`
            -   Only those things are configured which is not already configured in first step 1 (e.g. datasource)
-   JUnit
    -   `@Rule` annotation allows you reference a `TestRule` class which is setup/tearn down after before/after each test
        -   `TemporaryFolder`: Creates and deletes a temp folder for one test
        -   `OutputCapture`: Captures stdout and allows to do assertions on it

# 📅 16.08.2021 Security

-   **oAuth2**
    -   original goal: allow 3rd party applications to access users (e.g. google) data without having their password, it now rediects to the original service (e.g. google) which then returns a access token
    -   further advantage: also all first party apps are more secure because there does exist only one oauth server which has to be secured e.g. gmail login redirects to accounts.google. Also easier to refactor (e.g. 2f-auth) because there is only one server
    -   `client` is requesting a `token` at `authorization server` which in turn allows access `resource server` which is owned by `resource owner` (often you)
-   How to store passwords
    -   first only plaintext, then it was hashed, and then it was hashed with a salt (to avoid rainbow tables which hackers used to compare them with alreday hashed passwords. The salt ensures that everytime we have a new hash
    -   let spring decide on which passwords encoders to use([source](https://code-held.com/2021/05/15/spring-password-encoder/)): `DelegatingPasswordEncoder` will be updated according to best practice standards in security. Algorithm, salt etc. is encoded in the encoded string so it can also be updated dynamically while ensuring backwards compatibility (`Password Storage Format`)
-   Spring Security
    -   get UserDetails: `UserDetailsService`
        -   Spring security needs information what to check for authentication
        -   your Database and User representation is highly specific, a `UserDetailsService` abstracts this and only returns a `UserDetails` object

# 📅 13.08.2021 Tools and learnings

-   Version manager for all kinds of languages/tools: [asdf](https://github.com/asdf-vm/asdf)

# 📅 12.08.2021 Learnings and definitions around Spring

-   Definitions
-   Exclude field vom JSON reponse: `@JsonProperty(access = Access.WRITE_ONLY)` over the field
-   **JDBC**: All Java persistence is built on this. Lowest level
-   **JPA**: Agnostic way to do Java persistence without coupling your clients to Hibernate, etc.
-   **Hibernate**: object-relational mapping solution for Java environment
-   **Spring Data JPA**: Abstraction on top of Hibernate, e.g. no need to write DAO implementations
-   **DAO**: Data Access Object, you only create the DAO interface with method heads and the rest will be implemented
-   **DTO**: Data Transfer Object
    -   Is never a POJO since usually a framework provides the external system side formatting, e.g. @Entity (for db), @JsonProperty (for REST/JSON response)
    -   Decouple persistence models from API models: No messy attributes as @JSONIgnore, Mixing with persistence annotations, More difficult to create a Swagger out of it because you do not want to annotate your internal data model for the API description [source](https://stackoverflow.com/a/36175349)

# 📅 05.08.2021 Abbreviations

-   SA account: System administrator account

# 📅 05.08.2021 GCloud - Ressources in terraform

-   `google_storage_bucket`: create bucket in cloud storage service

-   `google_project_service`: Enable access for a project to a specific Google API service e.g. container registry

-   Cloud Build has a worker pool for doing the actual builds. For being able to access private ressources in your network you spawn your own private worker pool

-   `google_cloud_run_service`: Set routes and configurations for a network service: rollout policy, team ressource ownership - acts as a orchestrator

-   Questions

-   Difference between container and artifact registry?

# 📅 05.08.2021 More Terraform concepts

-   `locals`: like actual variables to resuse the same expression in the same module
-   first you need to enable certain api\'s for your project before you can create the ressources (`depends_on` needed)
-   `null_ressource`: A block of coded executed on a trigger or depends on statement

# 📅 04.08.2021 GCloud

-   source: [Google Glossary](https://cloud.google.com/terms/services)
-   \"Cloud Source Repositories\": provides git version controll
-   \"Cloud Build\": built environment and publish artifact somewhere
-   \"Cloud Logging\": log aggregation with error reporting features, search for \"logs explorer\"
-   \"Cloud Run: run stateless containers on a fully-managed environment, also manages thinks like replicas etc.
-   \"Cloud Ressource Manager\": Hierachical origanization of your Cloud resources, allows access controll and configuration settings
-   \"Service Networking API\": Set\'s up subnetworks, vpc\'s, DNS-Record Sets

# 📅 04.08.2021 Terraform

-   General idea
-   automate manage your infrastructure: platform and services
-   Steps
    -   first: infrastructure provisioning: like ec2 instances,users, docker installation, network, security, pipeline
    -   second: actual deployment
-   Terraform is used for the first step
-   Difference between Ansible and terraform:
    -   Terraform: mainly provisioning tool
    -   Ansible: only for configuration, more advanced/mature
-   Managing existing infrastructure
    -   create infrastructure
    -   changes to infrastructure
    -   replicating infrastructure (different environments)
-   How does Terraform connect to it\'s providers?
    -   Elements
        -   CORE figures out based on: 1) Local TF-Configs 2) State
        -   PROVIDERS: Like AWS, Kubernetes etc. with each having ressources
    -   Core then creates a execution plan to apply through providers
-   Commands
    -   `refresh`: Query providers to get current state
    -   `plan`: Creates an execution plan based in state
    -   `apply`: Execute plan
    -   `destroy`: Remove all ressources/infrastructures (e.g. for demo env)
-   Concepts - taken from [Terraform-Glossary](https://www.terraform.io/docs/glossary.html)
-   `ressource`: Representation of a provider ressource Terraform will create once declared
-   `data`: Retrieve data outside of Terraform, supplied to `ressource`
-   `module`: collection of Terraform configurations (can be parametrized via `variable`), a module has to be called by some other configuration in order to be applied to the state
-   `variable`: Key/Value pairs which can be injected into a module which is the used there (child module retrieves from parent module), Note: Never put hard-coded values in here. Also can be accessed via \"\${var.name}\" in all the modules
-   `backend`: Defines e.g. where the state is stored (allowing colloboration)
-   `output`: Module exporting data (can be shown to user or used by other module)

# 📅 29.06.2021 Mockito

-   Mock deeply nested object: `RETURNS_DEEP_STUPS`

# 📅 29.06.2021 team: Agile routines I like

-   Lake of feelings in [english](https://github.com/biocarl/img/blob/master/Lake%20of%20Feelings-english.png) and [german](https://github.com/biocarl/img/blob/master/Lake%20of%20Feelings.png)
-   Inbox
-   Walking the board
-   Sign-Ups

# 📅 29.06.2021 Tipps for facilitating retros\'s

-   Let people room to speak
-   Don\'t ask if it is ok what you are doing (you are the facilitator)
-   Don\'t ask closed question
-   Make people speak as soon as possible
-   do less items

# 📅 29.06.2021 IntelliJ Shortcuts

-   Use F2 to navigate to next error (Fn + f2)
-   Command E: Recent files
-   2 x CTRL: Run script from anywhere
-   Command + Shift + Enter: Fancy autocomplete
-   Controll T: See all refactor commands
-   Command P -\> show parameters
-   Multiple cursors ([source](https://stackoverflow.com/a/55221176))
    -   Go to vim emulation settings and set command G to Intelli
    -   Maybe set to hex input:
    -   \<Control G\>: highlight next match as multiple cursors
    -   \<Control + Command + G\>: Highlight them all at once

# 📅 29.06.2021 Vim: Folding

-   close single fold: `zc`
-   open single fold: `zo`
-   close all folds: `zR`
-   open all folds: `zM`

# 📅 29.06.2021 Prometheus

-   Read local memory `http://localhost:7979/metrics/jvm.memory.max?tag=area:heap` and `http://localhost:7979/metrics/jvm.memory.used?tag=area:heap`

# 📅 29.06.2021 How to find things // Data acquisition

-   Cloudsearch
-   Jira tickets from other teams
-   Company Documentation (tech, confluence,...)
-   Github
-   Chats/G-Groups
-   Always return to the initial onboarding documents - you might miss things

# 📅 29.06.2021 Useful links

-   E-Macs Shortcuts you can use in macOS: [link1](https://jblevins.org/log/kbd)
-   Jira-Formatting: [link1](https://jira.atlassian.com/secure/WikiRendererHelpAction.jspa?section=advanced) and [link2](https://jira.atlassian.com/secure/WikiRendererHelpAction.jspa?section=advanced)
-   Things you can do with [draw.io](https://drawio-app.com/interactive-diagrams-with-custom-links-and-actions/)
-   GSuite/Google Shortcuts: [Link](https://support.google.com/chat/answer/7649271?hl=en&authuser=0)

# 📅 29.06.2021 Useful bash/zsh alias

-   git push upstream: `gpsup`
-   git checkout -b: `gcb`
-   Git commands for undo changes
-   git reset --hard
-   git clean -f

# 📅 29.06.2021 Useful unix tools

-   edit and execute last command: `fc`

# 📅 29.06.2021 Useful docker commands

-   List CPU\'s: `docker ps -q | xargs  docker stats --no-stream`
-   Run local docker container: `docker run --publish 8090:8080 --env SPRING_PROFILES_ACTIVE=local IMAGE`
-   Delete all docker containers originating from one image: `docker rm -f $(docker ps -a -q  --filter ancestor=postgres:13)`
-   delete all docker containers: `docker rm -f $(docker ps -a -q)`

# 📅 29.06.2021 Useful kubectl commands

-   list the logs of a previously stopped pod: `kubectl logs --previous`
-   do something with a set of grep\'ed pods: `kubectl get pods | grep shard |  cut -d ' ' -f1 | xargs echo`
-   even better, you can use `up` ([github](https://github.com/akavel/up)), to check the results

# 📅 29.06.2021 Useful postgres commands

-   Show foreign tables and foreign servers: `\des+` and `\dE[S+]`
-   where logs are stored: `SHOW log_directory;`
-   Make a long running query: `select pg_sleep(5 * 60);`
-   Count connections: `select count(*) from pg_stat_activity;`
-   Sample data (for not to big table): 2. `COPY  (select * from table ORDER BY random() LIMIT 10000) TO '/home/postgres/export_10k.csv' CSV HEADER;`
-   List indexes: `select * from pg_indexes where table not like 'pg%';`

# 📅 29.06.2021 Sharding with fdw and pl-proxy

-   fdw does not parallelize shard access
-   uses flyway placeholders (via env variables or setting placeholders via fluid config)

``` {.sql}
create table table (
    name char(64) NOT NULL,
    id int NOT NULL,
) PARTITION by HASH (id);

CREATE EXTENSION IF NOT EXISTS postgres_fdw;

CREATE SERVER IF NOT EXISTS shard1 FOREIGN DATA WRAPPER postgres_fdw OPTIONS (dbname '${shard1_db_name}', host '${shard1_host}', port '${shard1_port}');
CREATE SERVER IF NOT EXISTS shard2 FOREIGN DATA WRAPPER postgres_fdw OPTIONS (dbname '${shard2_db_name}', host '${shard2_host}', port '${shard2_port}');

CREATE USER MAPPING IF NOT EXISTS FOR PUBLIC SERVER shard1 OPTIONS (user '${shard1_user}', password '${shard1_password}');
CREATE USER MAPPING IF NOT EXISTS FOR PUBLIC SERVER shard2 OPTIONS (user '${shard2_user}', password '${shard2_password}');

CREATE FOREIGN TABLE table_shard1 PARTITION OF table for values with (modulus 2, remainder 0) SERVER shard1 OPTIONS (table_name 'table');
CREATE FOREIGN TABLE table_shard2 PARTITION OF table for values with (modulus 2, remainder 1) SERVER shard2 OPTIONS (table_name 'table');

CREATE EXTENSION IF NOT EXISTS plproxy;

CREATE SERVER IF NOT EXISTS shards FOREIGN DATA WRAPPER plproxy OPTIONS (
    p0 'dbname=${shard1_db_name} host=${shard1_host} port=${shard1_port} application_name=plproxy user=${shard1_user} password=${shard1_password}',
    p1 'dbname=${shard2_db_name} host=${shard2_host} port=${shard2_port} application_name=plproxy user=${shard2_user} password=${shard2_password}'
    );

-- needed otherwise you can't provide username/password in server definition above
CREATE USER MAPPING IF NOT EXISTS for public SERVER shards OPTIONS (user '${shard1_user}');

CREATE OR REPLACE FUNCTION get_entry_by_name(p_name varchar(64))
    RETURNS TABLE (name char(64), id int) AS $$
    CLUSTER 'shards';
RUN ON ALL;
SELECT name, id FROM table WHERE name = p_name;
$$ LANGUAGE plproxy;
```

# 📅 29.06.2021 You can patch a deployment and also inject spring variables like so
-   [source](https://github.com/spring-projects/spring-boot/wiki/Relaxed-Binding-2.0#lists-1)
- `zkubectl patch deployment $DEPLOYMENT --patch "$(cat sharding-patch.yaml)"`

# 📅 25.06.2021 Change local host reference to maschine host in docker image
- `docker exec -u 0 $CONTAINER /bin/sh -c 'sed "s/127.0.0.1/$(dig +short host.docker.internal)/g" /etc/hosts > tmp.txt && cat tmp.txt > /etc/hosts'`

# 📅 11.06.2021 Show previous stashes
- `git stash show -p stash@{3}`

# 📅 11.06.2021 Java collectors and teeing operator
-   Combine two collectors

``` {.python}
HashMap<String, Employee> result = employeeList.stream().collect( 
                        Collectors.teeing(
                                Collectors.maxBy(Comparator.comparing(Employee::getSalary)),
                                Collectors.minBy(Comparator.comparing(Employee::getSalary)),
                                (e1, e2) -> {
                                    HashMap<String, Employee> map = new HashMap();
                                    map.put("MAX", e1.get());
                                    map.put("MIN", e2.get());
                                    return map;
                                }
                        ));
```

# 📅 11.06.2021 Postgres commands

-   Speed up index creation and maintenance work related processes

`SET maintenance_work_mem TO '1000 MB';` `SET max_parallel_maintenance_workers TO 5;`

# 📅 11.06.2021 Useful Kubernetes commands

-   Shell into db

`kubectl exec -it podname bash` `psql -U postgres -d db_name` // -c \"Direct string\" and -f \"Load from file\"

-   Edit deployment files in prod

`kubectl edit deployment DEPLOYMENT_ID` Sometimes needed `kubectl rollout restart deployment DEPLOYMENT_ID`

# 📅 11.06.2021 Postgres Theory

-   Disadvantage of using partitioning
-   if a a lot will impact query planner performance (over 500)
-   there are not global unique constraints, only uniqueness in a partition can be guaranteed
-   [Course](https://www.udemy.com/course/postgresql-high-performance-tuning-guide/) you want to take

# 📅 11.06.2021 GSuite short links

-   Docs \>\> create and collaborate on documents

`docs.new | doc.new | document.new`

-   Sheets \>\> create and collaborate on spreadsheets

`sheets.new | sheet.new | spreadsheet.new`

-   Slides \>\> create new powerful presentations

`slides.new | slide.new | presentation.new | deck.new`

-   Forms \>\> create forms, registrations, surveys and quizzes

`forms.new | form.new`

-   Calendar \>\> schedule a new event

`cal.new | meeting.new`

-   Meet \>\> make video conferences and share your screen

`meet.new`

-   Jamboard \>\> collaborate in real time on a digital whiteboard

`jam.new`

-   Sites \>\> create a website to share info with others

`site.new | sites.new | website.new`

-   Diagrams \>\> create, edit, and share diagrams (formerly known as draw.io)

`diagram.new | diagrams.new`

-   Keep \>\> create, edit, and share notes

`keep.new`

# 📅 30.04.2021 How to use Postgres EXPLAIN

-   What it is
-   executed plan generated by the optimizer
-   Parameters
-   `ANALYZE`: Be aware: Does also executes the query!
-   `BUFFERS`: works only together with ANALYZE, shows what buffer is used in each step
-   `VERBOSE`: Print each step in the execution plan
-   `SETTINGS`: Print all performance-relevant parameters which are different from their output

# 📅 24.03.2021 Postgres Performance Optimization

-   Tablespaces
-   Tablespaces are, in short, the way to tell the Postgres server where to place the physical files for SQL objects.
-   Other tips
-   Partitoning your table is also good since you can deploy \"multiple autovacuum workers on the same logical table\"

# 📅 16.03.2021 Roadmap for sharding

-   [source](https://www.youtube.com/watch?v=C4GJAjUcAtg)
-   Approaches
    -   Application-side sharding
    -   PL/Proxy: Remote procedure calls between databases (used by netflix)
    -   Postgres-Forks: Postgres-XC/XL, with distributed queries implemented (heaviliy modified)
    -   Citus: Postgres-Extension (heaviliy modified)
    -   Not postgres based, like hadoop
-   Replicated tables
    -   Small dictionaries you would have repliacted on each shard since it is quicker to look up and you do not need to do costly joins
-   Streaming replication
    -   Each shard will have replicated tables from other shards (shardman us doing this)

# 📅 09.03.2021 What you can do with LightStep

-   Terms
-   **ingress operations**: the first operations handling external requests from outside that service (starting out a trace)
-   **egress operations**: are those operations that call out to external services (ending the trace of a single service)

# 📅 09.03.2021 Basics of distributed tracing

-   Why?
-   increasingly more distributed infrastructures
-   microserver in isolation are easy to manage and understand but complexity arsises when interaction with its environment (distributed computing)
-   need for increasing visibility across teams
-   indentify bottlenecks in the system (adaptive paging)
-   global health of the system/detect root cause of a problem in a system
-   What?
-   is tracing a request accross multiple systems
-   tracing is a bunch of log messages which can be correlated together through a correlation id
-   distributed tracing starts with one request and following the flow other systems will do operations on it resulting in other traces, which itself is segmented in spans, unique actitivies performed by the system
-   spans can fork into child spans (for instance parallel processes) resulting in a span tree which in its totality represents the whole trace
-   Components
-   **Instrumentation**: The process of collecting data (a lot of automated tools)
-   **Trace context**: You need a unique ID passed along with timestamp to reconstruct the order
-   A trace contains
    -   spans (with component, operation, duration, other metadata)
    -   errors
-   **Analysis and visualization**: Frontend of telling the story of one trace. Standards like Opentracing/OpenCensus create a interface between metric collection (instrumentation) and frontend/analysis solutions
-   Observability: \"Observability lets you understand why something is wrong, compared with monitoring, which simply tells you when something is wrong.\"
-   Adaptive Paging
-   if there is one service down you will have a christmas tree (all components fire alarms), all incident teams will try to solve the issue but usually only one team can solve this (creates alarm fatigue)
-   solution, page the team closest to the problem

# 📅 25.02.2021 Database concepts

-   Views
-   is a named query, usually combines several base tables but does not store extra data (vs materialized view)
-   usefull to wrap complex queries
-   good for granting users only a subset of different base tables
-   consistent abstraction layers even if underlaying base tables change
-   Store procedures
-   Some kind of functions you can define to do complex operations in a batch
-   you can define control flows like if etc.
-   Elasticity
-   describes the flexibility how a distributed database can adapt to changes
-   changes could be adding/removing nodes or data models (which is rather fix for relational databases)

# 📅 23.02.2021 Sharding and Foreign Data Wrapper in Postgres

-   Theory
-   Is just a view to a external table, but looks like a local table
-   Parameters required:
    -   foreign server
    -   user mapping
    -   create a table: need to define how the foreign table looks like ok the remote side (but there is also the IMPORT FOREIGN SCHEMA option)
-   Facts
    -   there is always a head node, with all the fdw pointing to different shards (sometimes also called: data and coordinator nodes)
    -   the head/coordinator node is recieving the query is doing the planning and offloading analysis and queries to shards
    -   in the same way there is also the concept of parent and child transactions, same is the case for transactions (child will rollback, if parent does rollback)
    -   for high traffic we can have several coordinator nodes easliy since those nodes are stateless, all data is stored on the data nodes
    -   JOINS are done on the master, all the data has to be transferred therefore make sure you push where clauses down -\> seq scans can run on each shard?
        -   **Enabling parallelism on the coordinator**
            -   With PostgreSQL 9.6 [parallel queries](https://www.postgresql.org/docs/10/parallel-query.html) were introduced
            -   When optimal will create query plan (which is a [tree](https://tatiyants.com/postgres-query-plan-visualization/)) containing a gather/gather merge node which contains a single plan which is then executed in paralell
            -   This is done by spawning a bunch of background workers (including a leader which is reponsible of gathering the data)
            -   Gather nodes do not care about the ordering of the tuples generated by the workers and the leader merges them as they come, a merge gather node means that all workers and the leaders cares about the ordering
            -   gather merge nodes were added with v10, no need to have a parent sorting node anymore if you are interested in the order
            -   queries against several fdw are not parallized (current [state](https://www.postgresql.org/docs/12/parallel-safety.html)), each partition is scanned one after another - although there exists some [unofficial patch](https://github.com/swarm64/parallel-postgres-fdw-patch), [another one](https://pgxn.org/dist/pmpp/doc/pmpp.html), see also `IsForeignScanParallelSafe`
    -   It always inserts to whole table on the foreign server if this is the foreign table definitions (there are no defaults)
    -   you you run ANALYZE on the local system it will collect stats on the foreign system and bring them back to local
    -   Use presharding (read more \[[here](https://redis.io/topics/partitioning#presharding))
    -   Still do partitioning on shards, small tables are always good since it helps you to keep the index small or potentially even not needing one (seq scan is faster, no need to build b-tree and not random access)
    -   You can also fire procedures on the foreign server for example before every insert
-   About connections
    -   there is not connection pooling for the fdw in place, meaning if you have 12 incoming connections and 10 shards, your postgres backend has potentially 12\*10 outgoing connections
    -   but outgoing connections are cached (same connection is used for the incomming connection) (see [difference](https://stackoverflow.com/questions/5095884/what-is-the-difference-between-caching-and-pooling#:~:text=The%20distinction%20is%20usually%20drawn,See%20this%20explanation.&text=Caching%20usually%20refers%20to%20holding,of%20the%20value%20is%20expensive).))
    -   `fetch_size` is the number of rows to be transfered from master node to shard in one batch (100k performs well)
-   About backups
    -   doing backup of every slave/shard
    -   if there is transactions over several shards WAR based backup might be not that easy since consitency is key here
-   Current state of fdw
    -   lacks support for INSERT statements with an ON CONFLICT DO UPDATE clause
-   Useful commands for postgres
    -   `EXPLAIN (verbose) command` shows the also commands executed on foreign server
-   Usefull Sources
    -   this [video](https://www.youtube.com/watch?v=3JQrfgb3Av0)
    -   about a [elastic postgres solution](https://swarm64.com/post/scaling-elastic-postgres-cluster/)
    -   from gitlab [blog](https://about.gitlab.com/handbook/engineering/development/enablement/database/doc/fdw-sharding.html)

# 📅 16.02.2021 About databases

-   Table scans
-   INDEX SCAN: Go over index b-tree and afterwards potentially over heap if not available in non-key columns. Still can be quite expensive since fetching from Heap is a random access operation (which seq scan is not)
-   INDEX ONLY SCAN: Like above but everything you need is included in non-key cols (no HEAP needed)
-   BITMAP SCAN: First creates a bitmap of all indices who fufill the predicate and then bundles the heap access to not needing to much random access (working with offsets)
-   SEQUENTIAL SCAN: The classic full table scan
-   Sharding
-   Why sharding in the first place? Indicies grow large -\> longer queries -\> more cpu/memory
-   Unless your sharding field is a seq key you will need to ensure conistent hashing
-   Difference to horizontal sharding: it is still the same database, but different tables or even schema, client has to know those
-   Pros: Horizontally easy to scale + Security (e.g. a user only has access to one shard)
-   Cons: Complex for client to decide to which shard to talk to, how to deal with transactions which impact two shards at the same time? Rollbacks are very hard. Schema changes are hard. Joins across shards are slow. If key you are looking for is not sharding field it is very slow because you have to hit all shards
-   Interesting thoughts
-   Why do we have one billion rows in the first place? Can you design your data model differently?
-   What is the read/write ratio and what are the access patterns?
-   Vertical partiting in postgresql works out of the box - client does not have to worry
-   Sharding is especially usefull if there are many connections/clients to one service and it also get\'s a CPU/Memory problem
-   but for this you can also get some read replicas (but only if you don\'t write a lot)
-   Partitions still support transactions
-   Sharding has no ACID transactions
-   Re-Sharding is very complicated (because all client has to adapt when you have application layer sharding)
-   YouTube has introduced a service layer before it vitess.io

# 📅 15.02.2021 About databases

-   (DB Engineering)
-   You don\'t need heap fetches if you just select the index (super fast but useless)
-   Always avoid full table scans
-   For looking at the details of a query always do explain analyze QUERY
-   (Indexing)
-   create index employees~name~ on employees(name);
-   LIKE statements will always trigger a full select because b-tree can\'t be scanned on partial string
-   key column: the index itself, non-key column: Include the value in the index itself so that you don\'t have to jump to the location of the whole row

# 📅 23.10.2020 MongoDb

-   Setting up mongo db locally
    -   docker pull mongo
    -   docker run -p 27017:27017 -d mongo
-   Setting up mongo shell
    -   brew install mongodb-community-shell
    -   brew tap mongodb/brew
-   Shell into local mongodb
    -   mongo \"<mongodb://localhost:27017>\"
-   List all databases
    -   show dbs
    -   use local

# 📅 23.10.2020 queues: Deliver at least once principle

-   Messages emmited can be duplicated

# 📅 23.10.2020 queues: Dead letter queue

-   Store messages which are not valid in a separate place while allowing to the main queue to continue. Usually messages on a dlq are not retried

# 📅 09.10.2020 pandas: Rolling Window

-   Do a rolling window which is vectorized

``` {.python}
df["result"] = (
    df.groupby("date")
    .rolling(window=7, min_periods=1) # will try to find at least 1 non-nan value
    .mean(skipna=True)
    .shift((-1 * window) + 1) #trick to go backwards
    .reset_index(drop=True)
)
```

# 📅 09.10.2020 pandas: Melting

-   Convert columns into row values

``` {.python}
pd.melt(df, id_vars=["week"], value_name="items", var_name="country")
# id_vars: variables which stay as such
```

# 📅 09.10.2020 bash: A bash script for running functions

-   Source: @emilyagras
-   bash script.sh run flag

``` {.bash}
   #!/usr/bin/env bash
   __run() {
     if [ "$1" == "flag" ]; then
      echo "Hello! 🤓"
      exit
    fi
  }
# Using the code below, you can create any new function with two underscores (__hello-world) and it
# will be accessible as an argument for this script like: ./run hello-world
validate_args() {
  acceptable_args="$(declare -F | sed -n "s/declare -f __//p" | tr '\n' ' ')"

  if [[ -z $1 ]]; then
    echo "Must provide an argument"
    echo -e "Available commands:\n$(declare -F | sed -n "s/declare -f __/ - /p")"
    exit 1
  fi
  if [[ ! " $acceptable_args " =~ .*\ $1\ .* ]]; then
    echo "Invalid argument: $1"
    echo -e "Available commands:\n$(declare -F | sed -n "s/declare -f __/ - /p")"
    exit 1
  fi
}

CMD=${1:-}
shift || true
if validate_args ${CMD}; then
  __${CMD} $@
  exit 0
fi

```

# 📅 07.10.2020 vim: Use vim in unix pipe to do linewise operations

``` {.bash}
#vim.sh
vim - -esbnN -c "% $1" -c 'w!/dev/stderr|q!' 2>&1 >/dev/null # % denotes when using norm will be applied on each line
#usage:
cat source.txt | bash vim.sh "% norm dt[xf,xf]xwwdfnr " | bash vim.sh "g/>/d"
```

-   [source](https://blog.robertelder.org/use-vim-inside-a-unix-pipe-like-sed-or-awk/)

-   (vim-intelliJ) Use cowsay in IntelliJ

``` {.bash}
#cowsay
read output
cat <<EOF
-------$output
-------$parameters
EOF
#usage:
:<1,>!bash cowsay "parameter"
```

-   (vim-intelliJ) Use norm and g command in IntelliJ

``` {.bash}
#vim

#!/bin/bash
command=$(echo $@) # Catch parameters
while IFS= read -r line; do # Catch stream
       printf '%s\n' "$line" | vim - -esbnN -c "% $command" -c 'w!/dev/stderr|q!' 2>&1 >/dev/null # % denotes when using norm will be applied on each line
done

#usage:
'<,'>!./vim g/if/norm I---
```

# 📅 01.09.2020 pandas: Pandas merge and relational algebra

-   `on`: the column names to use for alligning the rows (has to be in left/right df)
-   `left_on/right_on`: as above but to use if they are different
-   `left_index/right_index`: as above but use the index as join key
-   `how`: specifies how to determine which keys are to be included in the resulting table
    -   `left` Use keys from left frame only
        -   Can result in several rows with the same key if the right side has several of those keys
        -   Can result in nan cells if the keys are only present on the left side and not on right side
    -   `right` Use keys from right frame only
    -   `outer` Use union of keys from both frames
    -   `inner` Use intersection of keys from both frames
-   `suffixes`: Overlapping columns which are not part of the keys are suffixed (tupel for left and right)
-   if there are non-uniqs on both sides it results in a cartesian product of both

# 📅 01.09.2020 data: Tidy Data

-   Denotes the concept of having a data matrix whereas each row is a observation and each column a variable and each cell a value.
-   Using the format makes column-wise calculations and combining data much easier

# 📅 01.09.2020 pandas: Cookbook examples

``` {.python}
# If condition matches assign 555 to the columns BBB, CCC
df.loc[df.AAA >= 5, ['BBB', 'CCC']] = 555
# Alternative: operates on bool series
df.where(df_mask, -1000)
# Filter dataframe by multiple criteria
Crit1 = df.AAA <= 5.5
Crit2 = df.BBB == 10.0
Crit3 = df.CCC > -40.0
AllCrit = Crit1 & Crit2 & Crit3
# Use dictionary to create a new column
categories = {1: 'Alpha', 2: 'Beta', 3: 'Charlie'}
df[new_cols] = df[source_cols].applymap(categories.get)
```

# 📅 09.08.2020 Pandas: Working with data frames

-   When you want to operate on a bunch values in a series you can use this notation
-   It seems to be a shorthand for apply

``` {.python}
# Example for replacing the whitespaces of all column names
df.columns.str.replace(' ','_') # Returns a series with updated column names (you just have to reassign it)
# A more common case - filtering
df.column1.str.contains("Hallo") # Returns a series of bools which then can be used as a mask
```

# 📅 09.08.2020 Pandas: Convert a catamorphic function to a homomorphic one

-   A function like `sum` acts as aggregator, if you want to maintain structure you can call the function like `transform('sum')` so it will pad cells with the same result
-   Very useful if you do something like `orders.groupby('orderid').itemprice.transform('sum')`, the result will have the same length as orders

# 📅 08.08.2020 Python: Use named subgroups and go functional in python

-   By naminging subgroups \`(?P\<name\>+̣)\` you can return a \`groupdict\` containing \<name,match\> pairs.

``` {.python}
dic_raw = open('data/cedict_ts.u8').readlines()
spec = re.compile("(?P<traditional>\w)\s(?P<simplified>\w)\s\[(?P<pinyin>.+)\]\s\/(?P<english>.+)\/$")

list(map(lambda line: spec.match(line).groupdict(),
        filter(lambda line: not re.match(r"^[#|%]", line) and spec.match(line), dic_raw)))


# file=decdict_ts.u8
# 
# #! date=2020-08-08T07:57:03Z
# #! time=1596873423
# 龐雜 庞杂 [pang2 za2] /enormously complex/a vast jumble/
# 龑 䶮 [yan3] /high and bright/
# 龒 龒 [long2] /old variant of 龍|龙[long2]/
# 龔 龚 [Gong1] /surname Gong/
#


```

-   Output

``` {.python}
[{'traditional': '㩐',
  'simplfied': '㩐',
  'pinyin': 'den4',
  'english': 'variant of 扽[den4]'},
  {'traditional': '㩗',
   'simplfied': '携',
  'pinyin': 'xie2',
  'english': 'old variant of 攜|携[xie2]'}]
```

# 📅 08.07.2020 Clojure: Use merge-with for conflicting hash-map merges

``` {.clojure}
(merge-with + {:a 1  :b 2} {:a 1  :b 2 :c 3})   
;; output {:c 3, :a 2, :b 4}
```

# 📅 03.06.2020 Clojure: Operate on only one of the key-value pairs in a hash-map

``` {.clojure}
(reduce-kv #(assoc %1 %2 (flatten %3)) {})
```

# 📅 02.06.2020 Clojure: Use matching groups when replacing with regex

``` {.clojure}
(str/replace % #"\{:([^\s]+)[^{^}]*\}" "<$1>")
;; input:  喝 act-on {:drink 茶 饮料 啤酒 水 牛奶}
;; output: 喝 act-on <drink>
(str/replace "<subject><predicate><object>" #"\<([a-z]+)\>" "<$1>&lt;$1></$1>")
;; This is very useful if you want to quote a xml element and at the same time not
```

# 📅 28.05.2020 Chrome: Make content of any website editable

-   `document.designMode = 'on'.`
-   This allows you to edit content of a website directly in the view without manipulating the dom tree via for instance the Chrome Developer Tools

# 📅 16.05.2020 unix: The zsh shell allows you to write to your own prompt!

-   `print -z echo Hello world`
-   I can see how this becomes very useful if you load syntax files and edit them before running them
-   You would put something like this in your `.zshrc`

``` {.zsh}
function edit(){
   print -z $(cat $1)
}
```

``` {.bash}
$ edit syntax
```

-   You can also try to reproduce this in other shells - [see stackoverflow ](https://unix.stackexchange.com/questions/213799/can-bash-write-to-its-own-input-stream/213821#213821)

# 📅 15.05.2020 english: Name of modifier keys

-   `Strg` (Steuerungstaste) 🇩🇪 == `Ctrl` (Control-Taste) 🇨🇭/🇬🇧
-   `⇧` == (Umschalttaste) 🇩🇪 == (Shift) 🇬🇧
-   `Alt` == (Alttaste) 🇩🇪 == (Alt key) 🇬🇧
-   `⇪` == (Feststelltaste) 🇩🇪 == (Caps Lock) 🇬🇧
-   `↹` == (Tabulatortaste) 🇩🇪 == (Tab key) 🇬🇧
-   `Fn` == (Fn-Taste) 🇩🇪 == (Fn key) 🇬🇧

# 📅 15.05.2020 english: parameter vs argument

-   parameter := is a variable in a method definition
-   argument := is the data you pass into the method\'s parameters when calling the method

# 📅 15.05.2020 english: Names of english symbols

-   \"round brackets\" `( )`
-   \"square brackets\" or \"box brackets\" `[ ]`
-   \"curly brackets\" `{ }`
-   \"angle brackets\" `< >`
-   (English) Other key symbols
-   **\~** Tilde
-   **\`** back quote
-   **!** sometimes bang
-   **\#** sharp, hash
-   **°** degree
-   \*^\*^ caret or circumflex
-   **&** ampersand

\- \* asterisk, star

-   **-** hyphen, minus, dash
-   **:** colon
-   \' apostrophe, single quote
-   **\<** sometimes less than
-   **.** period, dot, full stop

# 📅 14.05.2020 git: Initalize your `.gitignore`

-   `ls -a . >> .gitignore` Why did I take so long to start doing this? 🤔

# 📅 13.05.2020 Unix: Several commands

-   (textutil) Resolve wired encoding issues of text/html files
-   `textutil -convert txt *.html` batch processing (OSX)
-   (xargs) How to use xargs with a consecutive actions afterwards (like pipe)
-   Snippet: How to concat a large (!) number of textfiles
-   `find . -name "*.txt" -print0 | xargs -0 -I {} sh -c "echo {}; cat {} >> total.txt".`
-   (awk) Use ranges to only iterate over lines withing a certain `start` and `end` pattern
-   `awk '/start/, /end/ {action}'.` Can match several times
-   (awk) The `next` statement allows to go into the **else** case of the pattern match
-   `awk '/pattern/ {print $2;next} {print}' stripped.txt`
-   (vim) Show whitespace characters in vim
-   Toggle with `:set nolist//list`

# 📅 12.05.2020 Unix: More commands

-   (awk) Group matches inside gawk (this does not work in the mac version)
-   `brew install gawk`
-   `gawk { match($0, /#([0-9]+)/, arr); print arr[1] }`
-   (sed) A how to split sentences in seperate lines
-   `sed 's/[.!?]  */&\n/g' file.txt` where the `&` is the back reference to the match

# 📅 11.05.2020 Unix: awk commands

-   (awk) Basic commands
-   1.  Basic structure: `pattern {action}`
-   When the pattern matches the action is executed.
-   Either one of them can be ommited, resulting implicitly in a) in match all lines (default pattern) b) print whole line (default action)
-   `{print $2}` print second row of each line (implicit pattern)
-   `$3 == 10` print whole line which has 10 at the third row (implicit action)
-   1.  Built-in variables
-   **NF** := number of fields of current line
-   **NR** := nth line
-   Default delimiter is whitespace (for splitting (**FS**) and joining (**OFS**))
-   You can even change the definition of what a line is: **RS** - defaults to \"`\n`{=latex}\" (with the join analog **ORS**)
-   2.  Syntax for patterns
-   `/regex/` without \$, results implicitley in \$0 (whole line)
-   `$1 ~ /regex /` runs the regex on first column of the line
-   `NR=10, NR=20` example for ranges (executes action on lines 10 to 20)
-   3.  Some useful actions
-   String functions like gsub, substring
-   `{gsub (/pattern/, "to subsitute"); print}`
-   String concat: `{print $1 $2}` -\> one string \|\| `{print $1,$2}` -\> joined with OFS
-   You can execute external commands: `awk /Hallo/ {system ("touch " $2)}` text.txt
-   Append prints to specific files `{print $0 >>"file.txt"}` // pipe also works
-   we can define global variables: `{chars += length; print chars}`
-   Extended structure: `BEGIN {action} pattern {action} END {action}`
-   `awk '{chars += length;print} END {print "Total amount of chars: ",chars}' text.txt`
-   4.  Equivalent unix commands
-   `cat file.txt` == `awk '{print}'` (defaults to print \$0)
-   `grep /pattern/ file.txt` == `awk '/pattern/'`
-   `nl file.txt` == `awk 'print NR,$0'`

# 📅 10.05.2020 vim: Use surround.vim (default in evil-mode)
- In order to swap brackets or any flanking symbol (e.g. \" \", {}, \[\]) press `cs` `+` **(** for **(** as flanking symbol.

# 📅 07.05.2020 Trivia: Linguistics 101
- For some side project of mine I need to learn some specifics how syntax and semantics of a sentence play together.
-   Transitivity of verbs := A intransitive verb does not allow a direct object. Whereas a transitive verb requires at least one object.
-   Topic-prominent language := A language which is syntactically structured in a way so that it focus on the topic (the given, old information), followed by a comment (for instance how that changes into a new on information)

# 📅 06.05.2020 Clojure: Implement atom? for clj/cljs using reader conditionals
- Some language features are not implemented the same way in clojure and clojurescript. To use the same code base for both one might use reader conditionals.

``` {.clojure}
(defn atom? [x]
   #?(:clj (instance? clojure.lang.IAtom x)
      :cljs (instance? cljs.core.IAtom x)))

```

\~ by [vlaaad](https://clojureverse.org/t/creating-a-cljc-atom-function/3885/3)

**Bonus:** To make this work you need to change the file extension from `.clj/.cljs` to `.cljc`

# 📅 05.05.2020 Currying vs partial application
- **Partial application** means creating an intermediate function by already defining part of its arguments **Currying** means breaking down a function in a bunch of intermediate functions which take only one argument.
- *Partial application is when you curry a function, and use some, but not all of the resulting functions.* \~ [SpoonMaiser](https://stackoverflow.com/questions/218025/what-is-the-difference-between-currying-and-partial-application#comment87580_218055)

# 📅 04.05.2020 vim: Start using the jump list This is a huge productivity booster: Use `Ctrl-o` and `Ctrl-i` (in command mode) to move forwards/backwards through the jumplist. The jumplist is maintained project wide!
- With `:jumps` you can see where you are currently located in the jumplist. The relative number `N` of jumps allows you to go directly to a jump of interest `N` `Ctrl-o`.
- **Bonus:** If you are using this in Spacemacs a split window will open with the jump list and you can just click on the item - maintaining the split layout. I love this 💚

# 📅 03.05.2020 Clojure: How to use quote and break out of it (unquote-splicing).
- Super useful when you want to write clojure/clojurescript into a file.

``` {.clojure}
(eval (read-string (str `(+ ~@(take 10 (range)))))) ;; 45
```

# 📅 02.05.2020 unix: Set readline to vim mode

``` {.bash}
set -o vim
set -o emacs (default)
```

# 📅 03.03.2020 intellij: Debugging 101

-   `Frames`: lets you navigate in call stacks of the threads.
-   this is especially useful if you set a debug point in a method and want to know which params passed in parent evocations

# 📅 01.05.2020 Clojure: Compute 2-dimensional matrix
- First time I found a use case for partials. I proudly present my helper function I made:

``` {.clojure}
(defn map-matrix [transducer m l]
    "Outputs a 2-dimensional matrix (m x l), each
     entry resulting of the transducer function which takes x ∈ m, y ∈ l."
     (map (fn [x] (map (partial transducer x) l))m))

(map-matrix + [1 2 3] [100 200 300])
;; ((101 201 301) (102 202 302) (103 203 303))

(map-matrix str ["Hey " "Oi " "你好 "] ["John" "Leandro" "白虎"])
;; (("Hey John" "Hey Leandro" "Hey 白虎") ("Oi John" "Oi Leandro" "Oi 白虎") ("你好 John" "你好 Leandro" "你好 白虎"))

```

# 📅 30.04.2020 Spacemacs: Replace Clojure expression through its result
- , e w

# 📅 30.04.2020 Git: Delete last commit locally (with changes in working dir)
-   `git reset HEAD`

# 📅 30.04.2020 Clojure: Rprewalk-replace Use clojure.walk/prewalk-replace to globally replace a object in arbitrarily nested object

``` {.clojure}
(defn update-all-with [atom  name new-block]
  "Updates existing block with more general elements. Recieves an atom <s> block,
   a name of the block to be substituted, and the new block."
    (reset! atom (clojure.walk/prewalk-replace {name new-block} @atom))
  )
```