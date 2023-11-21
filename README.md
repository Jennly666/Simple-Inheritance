#include <iostream>
#include <string>

class Human {
protected:
    std::string name;
    int age;
public:
    Human(const std::string& name, int age) : name(name), age(age) {}
};
int main() {
    Human person1("Ivanov Bandit", 12);
    Human person2("Shket Sasha", 17);
}
