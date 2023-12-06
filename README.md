#include <iostream>
#include <cmath>
class Shape {
public:
    virtual void move(double dx, double dy) = 0;
    virtual void rotate(double angle) = 0;
    virtual void display() const = 0;
    virtual ~Shape() {}
};
class Circle : public Shape {
private:
    double radius;
    double centerX;
    double centerY;
public:
    Circle(double r, double x, double y) : radius(r), centerX(x), centerY(y) {}
    void move(double dx, double dy) override {
        centerX += dx;
        centerY += dy;
    }
    void rotate(double angle) override {
        // Немає необхідності для кола, оскільки обертання кола не змінює його форму
    }
    void display() const override {
        std::cout << "Коло - Радіус: " << radius << ", Центр: (" << centerX << ", " << centerY << ")\n";
    }
};
class Square : public Shape {
private:
    double sideLength;
    double centerX;
    double centerY;
public:
    Square(double s, double x, double y) : sideLength(s), centerX(x), centerY(y) {}
    void move(double dx, double dy) override {
        centerX += dx;
        centerY += dy;
    }
    void rotate(double angle) override {
        // Немає необхідності для квадрата, оскільки обертання квадрата не змінює його форму
    }
    void display() const override {
        std::cout << "Квадрат - довжина сторони: " << sideLength << ", Центр: (" << centerX << ", " << centerY << ")\n";
    }
};
class Rectangle : public Shape {
private:
    double length;
    double width;
    double centerX;
    double centerY;
public:
    Rectangle(double l, double w, double x, double y) : length(l), width(w), centerX(x), centerY(y) {}
    void move(double dx, double dy) override {
        centerX += dx;
        centerY += dy;
    }
    void rotate(double angle) override {
        // Здесь можна реалізувати логіку обертання прямокутника
        // Наприклад, можна змінити координати та розміри відповідно до кута обертання
    }
    void display() const override {
        std::cout << "Прямокутник - Довжина: " << length << "Ширина: " << width << ", Центр: (" << centerX << ", " << centerY << ")\n";
    }
};
int main() {
    Circle circle(5.0, 0.0, 0.0);
    Square square(4.0, 2.0, 3.0);
    Rectangle rectangle(6.0, 3.0, -1.0, -2.0);
    // Переміщення фігур
    circle.move(1.0, 2.0);
    square.move(-2.0, 1.0);
    rectangle.move(3.0, -1.0);
    // Виведення інформації про фігури
    circle.display();
    square.display();
    rectangle.display();
    return 0;
}
