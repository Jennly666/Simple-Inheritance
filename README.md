#include <iostream>
#include <string>

class Human {
protected:
    std::string name;
    int age;
public:
    Human(const std::string& name, int age) : name(name), age(age) {}

    std::string getName() const {
        return name;
    }

    void setName(const std::string& newName) {
        name = newName;
    }

    int getAge() const {
        return age;
    }

    void setAge(int newAge) {
        age = newAge;
    }
};

class iActions {
public:
    virtual void eat() = 0;
    virtual void sleep() = 0;
    virtual void work() = 0;
};

class Teacher : public Human, public iActions {
private:
    std::string subject;
    int experience;
public:
    Teacher(const std::string& name, int age) : Human(name, age) {}
    virtual void eat() { std::cout << "Я ем" << std::endl; }
    virtual void sleep() { std::cout << "Я сплю" << std::endl; }
    virtual void work() { std::cout << "Я работаю" << std::endl; }
    void teach() { std::cout << "Я преподаю" << std::endl; }
};

class Student : public Human, public iActions {
private:
    std::string university;
public:
    Student(const std::string& name, int age, const std::string& university)
        : Human(name, age), university(university) {}

    std::string getUniversity() const {
        return university;
    }

    void setUniversity(const std::string& newUniversity) {
        university = newUniversity;
    }
    virtual void eat() { std::cout << "Я не ем" << std::endl; }
    virtual void sleep() { std::cout << "Я не сплю" << std::endl; }
    virtual void work() { std::cout << "Я работаю" << std::endl; }
};

class Pervak : public Student {
private:
    int ballEge;
public:
    Pervak(const std::string& name, int age, const std::string& university)
        : Student(name, age, university) {}
    virtual void eat() { std::cout << "Я ем" << std::endl; }
    virtual void sleep() { std::cout << "Я не сплю" << std::endl; }
    virtual void work() { std::cout << "Я не работаю" << std::endl; }
    void cheat() { std::cout << "Я списываю" << std::endl; }
};

int main() {
    setlocale(LC_ALL, "Russian");
    Human person1("Ivanov Bandit", 12);
    Student person2("Shket Sasha", 17,"FEFU");
    Teacher person3("Ivan", 3);
    Pervak person4("Gosha", 2, "sakhgu");

    std::cout << person4.getAge() << std::endl;
    person4.setUniversity("college");
    person4.eat();
    person4.cheat();

    std::cout << person3.getName() << std::endl;
    person3.sleep();
    person3.teach();

    std::cout <<  person2.getAge() << std::endl;
    person2.work();
    person2.setName("Sipliy");

    person1.setAge(6);
}
