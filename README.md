# Student-Management-System
Development a task management app using stack, queue and linked list for task scheduling and undo operations
import java.util.*;

class Student {
    int rollNo;
    String name;
    int marks;

    Student(int rollNo, String name, int marks) {
        this.rollNo = rollNo;
        this.name = name;
        this.marks = marks;
    }
}

public class StudentManagementSystem {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        HashMap<Integer, Student> studentMap = new HashMap<>();

        while(true) {
            System.out.println("\n1. Add Student");
            System.out.println("2. Remove Student");
            System.out.println("3. Search Student");
            System.out.println("4. Display All Students (Sorted by Marks)");
            System.out.println("5. Exit");
            System.out.print("Enter choice: ");
            int choice = sc.nextInt();
            sc.nextLine();

            switch(choice) {
                case 1:
                    System.out.print("Enter Roll No: ");
                    int roll = sc.nextInt();
                    sc.nextLine();
                    System.out.print("Enter Name: ");
                    String name = sc.nextLine();
                    System.out.print("Enter Marks: ");
                    int marks = sc.nextInt();
                    sc.nextLine();

                    Student s = new Student(roll, name, marks);
                    studentMap.put(roll, s);
                    System.out.println(" Student Added!");
                    break;

                case 2:
                    System.out.print("Enter Roll No to remove: ");
                    int r = sc.nextInt();
                    if(studentMap.containsKey(r)) {
                        studentMap.remove(r);
                        System.out.println(" Student Removed!");
                    } else {
                        System.out.println(" Student not found!");
                    }
                    break;

                case 3:
                    System.out.print("Enter Roll No to search: ");
                    int sr = sc.nextInt();
                    if(studentMap.containsKey(sr)) {
                        Student st = studentMap.get(sr);
                        System.out.println("Found: Roll " + st.rollNo + ", Name " + st.name + ", Marks " + st.marks);
                    } else {
                        System.out.println(" Student not found!");
                    }
                    break;

                case 4:
                    if(studentMap.isEmpty()) {
                        System.out.println("No Students Available!");
                        break;
                    }
                    List<Student> studentList = new ArrayList<>(studentMap.values());
                    studentList.sort((a, b) -> b.marks - a.marks); // Descending order

                    System.out.println(" Students Sorted by Marks:");
                    for(Student st : studentList) {
                        System.out.println("Roll: " + st.rollNo + ", Name: " + st.name + ", Marks: " + st.marks);
                    }
                    break;

                case 5:
                    System.out.println("Exiting...");
                    sc.close();
                    return;

                default:
                    System.out.println(" Invalid Choice!");
            }
        }
    }
}
