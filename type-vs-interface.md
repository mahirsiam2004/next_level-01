Type Alias vs Interface in TypeScript

Introduction
Type and interface are used to define the structure of data in TypeScript. Whilst they can appear quite similar in practice there are some key differences between the two.

Key Differences
An interface can only be used for objects whilst type can be used for anything including primitives, unions, tuples etc.

tstype Status = "active" | "inactive"; // Only possible with Type Alias in TypeScript
type Point = [number, number]; // Tuple Type Alias

Interface can be merged together by using the same name. Type aliases cannot be merged and will throw an error about the duplicate identifier.

tsinterface User { name: string }
interface User { age: number }
// User now has properties name and age.

Interfaces can be extended using extends whilst Types use intersections.

tsinterface Admin extends User { role: string }
type SuperAdmin = User & { permissions: string[] };

When to use them
Use interface when defining object structures, implementing classes and public API's from libraries. As they can be merged they are extensible. Use type when defining unions, tuples, mapped types, conditional types and function signatures.

Conclusion
No clear winner here! Try to use interface for objects and classes. Type should be used for unions and complex type operations. Just try to be consistent!