# Lambda & Stream

```java

@FunctionalInterface
interface CheckPerson {
    boolean test(Person p);
}

@FunctionalInterface
interface Printer {
    void test(Object o);
}

class CheckPersonWithCondition implements CheckPerson {

    @Override
    public boolean test(Person p) {
        return p.gender == Person.Gender.MALE;
    }

}

class ObjectPrinter implements Printer {

    @Override
    public void test(Object o) {
        System.out.println(o.toString());
    }
}

public class App {

    public static void main(String[] args) throws Exception {

        List<Person> peoples = Person.generatePersonList();

        System.out.println(peoples);

        // Condition for Male
        printPeopleWithCheck(peoples, new CheckPersonWithCondition());

        // Condition for Female
        printPeopleWithCheck(peoples, new CheckPerson() {
            @Override
            public boolean test(Person p) {
                return p.gender == Person.Gender.FEMALE;
            }
        });

        // With Lambda Expression for Male
        printPeopleWithCheck(peoples, p -> p.gender == Person.Gender.MALE);

        // With Predicatefor Female
        printPeopleWithCheckWithPredicate(peoples, p -> p.gender == Person.Gender.FEMALE);

        List<Person> personList = Person.generatePersonList();

        personList.forEach(System.out::println);

        List<Person> newList = personList.stream().map(
                x -> new Person(
                        x.getName(),
                        x.getAge() + 1,
                        x.getEmailAddress(),
                        x.getGender()))
                .collect(Collectors.toList());

        List<Person> anotherList = personList.stream()
                .filter(x -> x.getGender() == Person.Gender.FEMALE)
                .collect(Collectors.toList());

        List<Person> randomList = personList.stream()
                .sorted(Comparator.comparing(Person::getAge))
                .collect(Collectors.toList());

        System.out.println(newList);
        System.out.println(anotherList);
        System.out.println(randomList);

        ObjectPrinter objPrinter = new ObjectPrinter();
        objPrinter.test(10);

        App.appPrinter(10, System.out::println);

        Runnable runnable = () -> {
            System.out.println("hello world");
        };

        new Thread(runnable).start();
        System.out.println("another hello");

        Printer printer = (i) -> {
            System.out.println("Number is : " + i);
        };

        printer.test(21);

        List<Integer> arrlist = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
        List<Integer> evenList = arrlist.stream().filter(i -> i % 2 == 0).collect(Collectors.toList());
        List<Integer> revSortedList = arrlist.stream().sorted(Comparator.reverseOrder()).collect(Collectors.toList());
        List<Integer> naturalSortedList = revSortedList.stream().sorted(Comparator.naturalOrder())
                .collect(Collectors.toList());

        System.out.println(evenList);
        System.out.println(revSortedList);
        System.out.println(naturalSortedList);

    }

    public static void printPeopleWithCheck(List<Person> people, CheckPerson checkPerson) {
        for (Person p : people) {
            if (checkPerson.test(p)) {
                p.printPerson();
            }
        }
    }

    public static void printPeopleWithCheckWithPredicate(List<Person> people, Predicate<Person> checkPerson) {
        for (Person p : people) {
            if (checkPerson.test(p)) {
                p.printPerson();
            }
        }
    }

    public static void appPrinter(Object o, Printer genericPrinter) {
        genericPrinter.test(o);
    }
}

// Person.java
import java.util.ArrayList;
import java.util.List;

class Person {

    public enum Gender {
        MALE, FEMALE
    }

    Gender gender;

    String name;
    int age;
    String emailAddress;

    public Person() {
    }

    public Person(String name, int age, String emailAddress, Gender gender) {
        this.name = name;
        this.age = age;
        this.emailAddress = emailAddress;
        this.gender = gender;
    }

    public Gender getGender() {
        return gender;
    }

    public void setGender(Gender gender) {
        this.gender = gender;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String getEmailAddress() {
        return emailAddress;
    }

    public void setEmailAddress(String emailAddress) {
        this.emailAddress = emailAddress;
    }

    @Override
    public String toString() {
        return "Person{" +
                "gender=" + gender +
                ", name='" + name + '\'' +
                ", age=" + age +
                ", emailAddress='" + emailAddress + '\'' +
                '}';
    }

    public void printPerson() {
        System.out.println(this.toString());
    }

    public static List<Person> generatePersonList() {
        List<Person> people = new ArrayList<>();

        people.add(new Person("Uday Yadav", 21, "udayyadav@earth.com", Gender.MALE));
        people.add(new Person("Another Uday", 22, "yadavuday@earth.com", Gender.MALE));
        people.add(new Person("Multiverse Uday", 19, "multiuday@muultiverse.com", Gender.FEMALE));

        return people;
    }

}


```
