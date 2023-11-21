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

class Student : public Human {
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
};

int main() {
    Human person1("Ivanov Bandit", 12);
    Student person2("Shket Sasha", 17,"FEFU");
    person2.setName("Vadim");
    std::cout << person2.getUniversity() << std::endl;
}
