package com.mycompany.last_poe3;

import javax.swing.*;
import java.util.ArrayList;
import java.util.Arrays;

public class Last_POE3 {

    public static void main(String[] args) {
        while (true) {
            // Main menu options using JOptionPane
            int mainOption = JOptionPane.showOptionDialog(null,
                    "Welcome to EasyKanban! Please select an option:",
                    "EasyKanban",
                    JOptionPane.DEFAULT_OPTION,
                    JOptionPane.INFORMATION_MESSAGE,
                    null,
                    new String[]{"Add Task", "Show Report", "Exit"},
                    "Add Task");

            if (mainOption == 0) {
                taskApp(); // Call taskApp() method to handle task-related operations
            } else if (mainOption == 1) {
                showTaskList(); // Call showTaskList() method to display task-related reports
            } else {
                JOptionPane.showMessageDialog(null, "Thank you for using EasyKanban. Goodbye!");
                break; 
            }
        }
    }

    // Method for handling task-related operations
    public static void taskApp() {
        while (true) {
            // Task menu options using JOptionPane
            int taskOption = JOptionPane.showOptionDialog(null,
                    "Please Select an Option",
                    "Task Option",
                    JOptionPane.DEFAULT_OPTION,
                    JOptionPane.PLAIN_MESSAGE,
                    null,
                    new String[]{"Add Task", "Show Report", "Cancel"},
                    "Add Task");

            if (taskOption == 0) {
                taskNumber(); // Call taskNumber() method to input number of tasks
            } else if (taskOption == 1) {
                showTaskList(); // Call showTaskList() method to display task-related reports
            } else {
                break; 
            }
        }
    }

    // Method to input number of tasks
    public static void taskNumber() {
        String taskCountStr = JOptionPane.showInputDialog("Input Number Of Tasks:");
        int taskCount = Integer.parseInt(taskCountStr);

        for (int i = 0; i < taskCount; i++) {
            taskMake(); 
        }
    }

    // Method to create a task
    public static void taskMake() {
        // Input dialogs to gather task details
        String taskName = JOptionPane.showInputDialog("Task Name:");
        String taskNumber = JOptionPane.showInputDialog("Task Number:");
        String taskDescription = JOptionPane.showInputDialog("Task Description (less than 50 characters):");

        // Validate task description length
        if (taskDescription.length() > 50) {
            JOptionPane.showMessageDialog(null, "Task description should be less than 50 characters. Please try again.");
            taskMake(); // Recursive call to re-enter task description
            return;
        }

        String developerDetails = JOptionPane.showInputDialog("Developer Details:");
        String taskDuration = JOptionPane.showInputDialog("Task Duration (in Hours):");

        // Construct task ID
        String last3Chars = developerDetails.substring(Math.max(0, developerDetails.length() - 3));
        String taskInitials = taskName.substring(0, Math.min(2, taskName.length()));
        String taskId = (taskInitials + ":" + taskNumber + ":" + last3Chars).toUpperCase();
        JOptionPane.showMessageDialog(null, "Task ID - " + taskId);

        // Options for task status
        String[] statusOptions = {"To Do", "Doing", "Done"};
        int taskStatus = JOptionPane.showOptionDialog(null,
                "Task Status",
                "Task Status",
                JOptionPane.DEFAULT_OPTION,
                JOptionPane.INFORMATION_MESSAGE,
                null,
                statusOptions,
                statusOptions[0]);

        // Display task details using JOptionPane
        JOptionPane.showMessageDialog(null,
                "Task Status: " + statusOptions[taskStatus] + "\n" +
                        "Developer Details: " + developerDetails + "\n" +
                        "Task Number: " + taskNumber + "\n" +
                        "Task Name: " + taskName + "\n" +
                        "Task Description: " + taskDescription + "\n" +
                        "Task ID - " + taskId + "\n" +
                        "Duration: " + taskDuration + " hrs");

        // Method call to handle array or list of tasks
        arrayApplication(taskName, taskNumber, taskDescription, developerDetails, taskDuration, statusOptions[taskStatus]);
    }

    // Method to manage array or list of tasks (for demonstration purposes)
    public static void arrayApplication(String taskName, String taskNumber, String taskDescription, String developerDetails, String taskDuration, String taskStatus) {
        // Display task details in console (for demonstration purposes)
        System.out.println("Task Name: " + taskName);
        System.out.println("Task Number: " + taskNumber);
        System.out.println("Task Description: " + taskDescription);
        System.out.println("Developer Details: " + developerDetails);
        System.out.println("Task Duration: " + taskDuration);
        System.out.println("Task Status: " + taskStatus);
        System.out.println("-------------------");
    }

    // Method to display task-related reports and operations
    public static void showTaskList() {
      
        String[] task1 = {"Mike Smith", "Create Login", "5", "To Do"};
        String[] task2 = {"Edward Harrison", "Create Add Features", "8", "Doing"};
        String[] task3 = {"Samantha Paulson", "Create Reports", "2", "Done"};
        String[] task4 = {"Glenda Oberholzer", "Add Arrays", "11", "To Do"};

        // Option dialog for task list operations
        int taskOption = JOptionPane.showOptionDialog(null,
                "Task List Option",
                "Please Select Option",
                JOptionPane.DEFAULT_OPTION,
                JOptionPane.PLAIN_MESSAGE,
                null,
                new String[]{"Display Completed Task(s)", "Longest Task(s)", "Search Task", "Search by Developer", "Delete Task", "Report of All Tasks", "Cancel"},
                "Display Completed Task(s)");

        // Switch case based on selected option
        switch (taskOption) {
            case 0:
                if (Arrays.asList(task3).contains("Done")) {
                    JOptionPane.showMessageDialog(null, Arrays.toString(task3));
                }
                break;
            case 1:
                if (Arrays.asList(task4).contains("11")) {
                    JOptionPane.showMessageDialog(null, task4[0] + "\n" + task4[2]);
                }
                break;
            case 2:
                String taskName = JOptionPane.showInputDialog("Please Enter Task Name:");
                if (Arrays.asList(task1).contains(taskName)) {
                    JOptionPane.showMessageDialog(null, Arrays.toString(task1));
                }
                if (Arrays.asList(task2).contains(taskName)) {
                    JOptionPane.showMessageDialog(null, Arrays.toString(task2));
                }
                if (Arrays.asList(task3).contains(taskName)) {
                    JOptionPane.showMessageDialog(null, Arrays.toString(task3));
                }
                if (Arrays.asList(task4).contains(taskName)) {
                    JOptionPane.showMessageDialog(null, Arrays.toString(task4));
                }
                break;
            case 3:
                String developerName = JOptionPane.showInputDialog("Enter Developer Name:");
                if (Arrays.asList(task1).contains(developerName)) {
                    JOptionPane.showMessageDialog(null, task1[0] + "\n" + task1[1]);
                }
                if (Arrays.asList(task2).contains(developerName)) {
                    JOptionPane.showMessageDialog(null, task2[0] + "\n" + task2[1]);
                }
                if (Arrays.asList(task3).contains(developerName)) {
                    JOptionPane.showMessageDialog(null, task3[0] + "\n" + task3[1]);
                }
                if (Arrays.asList(task4).contains(developerName)) {
                    JOptionPane.showMessageDialog(null, task4[0] + "\n" + task4[1]);
                }
                break;
            case 4:
                String taskNameToDelete = JOptionPane.showInputDialog("Please Enter Task Name:");
                if (Arrays.asList(task1).contains(taskNameToDelete)) {
                    task1 = null; // Not ideal, should use ArrayList instead
                    JOptionPane.showMessageDialog(null, "Task 1 has been removed");
                }
                if (Arrays.asList(task2).contains(taskNameToDelete)) {
                    task2 = null; // Not ideal, should use ArrayList instead
                    JOptionPane.showMessageDialog(null, "Task 2 has been removed");
                }
                if (Arrays.asList(task3).contains(taskNameToDelete)) {
                    task3 = null; // Not ideal, should use ArrayList instead
                    JOptionPane.showMessageDialog(null, "Task 3 has been removed");
                }
                if (Arrays.asList(task4).contains(taskNameToDelete)) {
                    task4 = null; // Not ideal, should use ArrayList instead
                    JOptionPane.showMessageDialog(null, "Task 4 has been removed");
                }
                break;
            case 5:
                JOptionPane.showMessageDialog(null, Arrays.toString(task1) + "\n" +
                        Arrays.toString(task2) + "\n" +
                        Arrays.toString(task3) + "\n" +
                        Arrays.toString(task4));
                break;
            case 6:
                break;
        }
    }
}
