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

int main() {
    Human person1("Ivanov Bandit", 12);
    Human person2("Shket Sasha", 17);
    person1.setAge(22);
    person2.setName("Anton");
    std::cout << person1.getAge() << std::endl;
    std::cout << person2.getName();
}
