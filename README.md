<img width="841" height="893" alt="image" src="https://github.com/user-attachments/assets/2915c6d9-98c7-41f5-8f53-4694c931b328" />
<br>
<img width="489" height="118" alt="image" src="https://github.com/user-attachments/assets/aaa13b28-7917-4d49-ac5a-78b87ffd66ff" />
<br>
<img width="1120" height="909" alt="image" src="https://github.com/user-attachments/assets/00e39176-b28e-4d4f-91d9-2ac48956b824" />
<br>
<img width="768" height="109" alt="image" src="https://github.com/user-attachments/assets/02d1cbad-9c41-47e2-8a88-e3a131a42173" />
<br>






//2
let userTuple: [string, number, boolean] = ["Alex", 25, true];

function welcome(data: { name: string }): string {
    return `Добро пожаловать, ${data.name}!`;
}

interface IProduct {
    id: number;
    name: string;
    price: number;
    quantity: number;
}

abstract class BaseStore {
    abstract storeName: string;
}

class ProductStore extends BaseStore {
    storeName = "My Tech Store";
    private products: IProduct[] = [];

    private categories: Record<string, string> = {
        "elec": "Электроника",
        "book": "Книги"
    };

    addProduct(p: IProduct): void {
        this.products.push(p);
    }

    get allProducts() {
        return this.products;
    }

    updateQuantity(id: number, qty: number): void {
        const p = this.products.find(item => item.id === id);
        if (p) p.quantity = qty;
    }

    deleteProduct(id: number): void {
        this.products = this.products.filter(p => p.id !== id);
    }
}

const catalog: IProduct[] = [
    { id: 1, name: "Phone", price: 500, quantity: 10 },
    { id: 2, name: "Laptop", price: 1200, quantity: 5 }
];

const expensiveItems = catalog.filter(p => p.price > 600);
const totalPrice = catalog.reduce((sum, p) => sum + (p.price * p.quantity), 0);
//1
enum UserRole {
    Admin = "Admin",
    Teacher = "Teacher",
    Student = "Student"
}

interface User {
    readonly id: string | number; 
    name: string;
    role: UserRole;
}

type Course = {
    title: string;
    duration: number;
};

function printUserInfo(user: User): void {
    console.log(`Пользователь: ${user.name}, Роль: ${user.role}`);
}

const users: User[] = [
    { id: 1, name: "Ivan", role: UserRole.Admin },
    { id: "2", name: "Anna", role: UserRole.Student },
    { id: 3, name: "Max", role: UserRole.Teacher }
];

const students = users.filter(u => u.role === UserRole.Student);

function createUser(name: string, age?: number): string {
    return age ? `${name}, возраст: ${age}` : name;
}

function greet(message: string = "Привет"): void {
    console.log(message);
}

class CourseManager {
    private courses: Course[] = [];

    addCourse(course: Course): void {
        this.courses.push(course);
    }

    deleteCourse(title: string): void {
        this.courses = this.courses.filter(c => c.title !== title);
    }

    listCourses(): void {
        console.log("Список курсов:", this.courses);
    }
}
