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
    iActions() { std::cout << "iActions object created" << std::endl; }
    virtual ~iActions() {}

    virtual void eat() = 0;
    virtual void sleep() = 0;
    virtual void work() = 0;
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

class Teacher : public Human, public iActions {
public:
    virtual void eat() { std::cout << "Я ем" << std::endl; }
    virtual void sleep() { std::cout << "Я сплю" << std::endl; }
    virtual void work() { std::cout << "Я работаю" << std::endl; }
};

class Pervak : public Student {
public:
    virtual void eat() { std::cout << "Я ем" << std::endl; }
    virtual void sleep() { std::cout << "Я не сплю" << std::endl; }
    virtual void work() { std::cout << "Я не работаю" << std::endl; }
};

int main() {
    setlocale(LC_ALL, "Russian");
    Human person1("Ivanov Bandit", 12);
    Student person2("Shket Sasha", 17,"FEFU");
    person2.setName("Vadim");
    std::cout << person2.getUniversity() << std::endl;
    person2.sleep();
}
