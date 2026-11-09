# Combining Union and Intersection Types in TypeScript

## 1. Introduction

TypeScript provides different types to make JavaScript code safer and easier to maintain. Union and Intersection types are useful features that allow developers to combine multiple types. They help us define flexible and reusable data structures.

## 2. What is a Union Type?

A Union Type allows a variable to hold values of two or more different types. We use the pipe (`|`) operator to create a union.

```ts
type ID = string | number;

function displayID(id: ID): void {
    console.log(id);
}

displayID(101);
displayID("USER-101");
```

Here, the `id` parameter can accept either a string or a number.

## 3. What is an Intersection Type?

An Intersection Type combines multiple types into one. We use the ampersand (`&`) operator. The resulting type must contain all required properties from the combined types.

```ts
type Person = {
    name: string;
};

type Employee = {
    salary: number;
};

type Staff = Person & Employee;

const staff: Staff = {
    name: "Rahim",
    salary: 30000
};
```

Here, `Staff` requires both `name` and `salary`.

## 4. Core Differences

Union means a value can match one of the available types. Intersection means a value must satisfy all combined types. Use Union when a value can have different forms. Use Intersection when you need to combine multiple object structures.

## 5. Combining Union and Intersection Types

We can combine both operators to create flexible structures for real-world applications.

```ts
type Admin = {
    name: string;
    permissions: string[];
};

type Customer = {
    name: string;
    email: string;
};

type Account = Admin | Customer;

type VerifiedAdmin = Admin & {
    isVerified: boolean;
};

const admin: VerifiedAdmin = {
    name: "Karim",
    permissions: ["read", "write"],
    isVerified: true
};
```

In this example, `Account` accepts either an Admin or a Customer. However, `VerifiedAdmin` requires all Admin properties and an additional `isVerified` property.

## 6. Conclusion

Union and Intersection types make TypeScript more powerful and flexible. Union allows multiple possible types, while Intersection combines multiple requirements. Understanding both helps developers create reusable, type-safe, and maintainable applications.