# Personal-Fitness-Workout-Tracker
The Personal Fitness &amp; Workout Tracker is a Java-based desktop application designed to help users monitor and manage their daily fitness activities, workout routines, and health progress. The system allows users to log exercises, track calories burned, set fitness goals, and monitor their progress over time.

The Personal Fitness & Workout Tracker is a Java-based application designed to help users record and manage their daily fitness activities. The system allows users to store workout details such as exercise name, duration, repetitions, sets, and other relevant fitness information. It provides a simple way to organize workout records and monitor fitness activities over time.

The application is developed using Java programming concepts such as classes, objects, methods, arrays, conditional statements, loops, and file handling. The project demonstrates how core Java concepts can be applied to develop a practical fitness-management application. The main objective is to provide a simple, user-friendly system for maintaining workout information and encouraging consistent fitness tracking.

The system can also help users maintain a structured history of their workouts, making it easier to review previous activities and track progress. By organizing fitness data in a systematic manner, the application reduces the need for manual record keeping and provides quick access to stored information. The project focuses on applying Java programming techniques to solve a real-world problem while developing skills in object-oriented programming, data management, and application design.


Team Members --> 2620090080 Varun Kowshik, 2620030360 Grahith, 2620030540 Mohith
Coordinator --> Dr K.Rakesh




Code goes here -->

import java.util.Scanner;

public class Personal-Fitness-and-Health-Tracker {

    static Scanner sc = new Scanner(System.in);

    static String[] workout = new String[50];
    static int[] duration = new int[50];
    static int count = 0;

    public static void main(String[] args) {

        int choice;

        do {
            System.out.println("\n===== PERSONAL FITNESS & WORKOUT TRACKER =====");
            System.out.println("1. Add Workout");
            System.out.println("2. View Workouts");
            System.out.println("3. Calculate BMI");
            System.out.println("4. Show Total Workout Time");
            System.out.println("5. Exit");
            System.out.print("Enter your choice: ");

            choice = sc.nextInt();
            sc.nextLine();

            switch (choice) {

                case 1:
                    addWorkout();
                    break;

                case 2:
                    viewWorkouts();
                    break;

                case 3:
                    calculateBMI();
                    break;

                case 4:
                    totalTime();
                    break;

                case 5:
                    System.out.println("Thank you for using the Fitness Tracker!");
                    break;

                default:
                    System.out.println("Invalid choice!");
            }

        } while (choice != 5);
    }

    static void addWorkout() {

        if (count == 50) {
            System.out.println("Workout limit reached.");
            return;
        }

        System.out.print("Enter workout name: ");
        workout[count] = sc.nextLine();

        System.out.print("Enter duration in minutes: ");
        duration[count] = sc.nextInt();

        count++;

        System.out.println("Workout added successfully!");
    }

    static void viewWorkouts() {

        if (count == 0) {
            System.out.println("No workouts recorded.");
            return;
        }

        System.out.println("\n----- WORKOUT HISTORY -----");

        for (int i = 0; i < count; i++) {
            System.out.println((i + 1) + ". " +
                    workout[i] + " - " +
                    duration[i] + " minutes");
        }
    }

    static void calculateBMI() {

        System.out.print("Enter weight in kg: ");
        double weight = sc.nextDouble();

        System.out.print("Enter height in meters: ");
        double height = sc.nextDouble();

        double bmi = weight / (height * height);

        System.out.printf("Your BMI is: %.2f%n", bmi);

        if (bmi < 18.5)
            System.out.println("Category: Underweight");
        else if (bmi < 25)
            System.out.println("Category: Normal");
        else if (bmi < 30)
            System.out.println("Category: Overweight");
        else
            System.out.println("Category: Obese");
    }

    static void totalTime() {

        int total = 0;

        for (int i = 0; i < count; i++) {
            total += duration[i];
        }

        System.out.println("Total workout time: " + total + " minutes");
    }
}
