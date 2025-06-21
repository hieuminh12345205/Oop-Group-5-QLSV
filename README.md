# Oop-Group-5-QLSV
// Simple Student Management Console App in C#
using System;
using System.Collections.Generic;

class Student
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Major { get; set; }
    public double GPA { get; set; }

    public override string ToString()
    {
        return $"ID: {Id}, Name: {Name}, Major: {Major}, GPA: {GPA:F2}";
    }
}

class Program
{
    static List<Student> students = new List<Student>();
    static int nextId = 1;

    static void Main()
    {
        while (true)
        {
            Console.Clear();
            Console.WriteLine("=== Student Management App ===");
            Console.WriteLine("1. Add Student");
            Console.WriteLine("2. View Students");
            Console.WriteLine("3. Search by Name");
            Console.WriteLine("4. Exit");
            Console.Write("Choose an option: ");

            string input = Console.ReadLine();
            switch (input)
            {
                case "1": AddStudent(); break;
                case "2": ViewStudents(); break;
                case "3": SearchStudent(); break;
                case "4": return;
                default: Console.WriteLine("Invalid option. Press Enter to try again."); Console.ReadLine(); break;
            }
        }
    }

    static void AddStudent()
    {
        Console.Write("Enter name: ");
        string name = Console.ReadLine();
        Console.Write("Enter major: ");
        string major = Console.ReadLine();
        Console.Write("Enter GPA: ");
        double gpa = double.Parse(Console.ReadLine());

        students.Add(new Student { Id = nextId++, Name = name, Major = major, GPA = gpa });
        Console.WriteLine("Student added! Press Enter to continue...");
        Console.ReadLine();
    }

    static void ViewStudents()
    {
        Console.WriteLine("\n--- Student List ---");
        foreach (var s in students)
            Console.WriteLine(s);
        Console.WriteLine("Press Enter to continue...");
        Console.ReadLine();
    }

    static void SearchStudent()
    {
        Console.Write("Enter name to search: ");
        string keyword = Console.ReadLine().ToLower();
        Console.WriteLine("\n--- Search Results ---");
        foreach (var s in students)
        {
            if (s.Name.ToLower().Contains(keyword))
                Console.WriteLine(s);
        }
        Console.WriteLine("Press Enter to continue...");
        Console.ReadLine();
    }
}
