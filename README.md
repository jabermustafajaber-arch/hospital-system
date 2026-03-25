import java.util.ArrayList;
import java.util.List;

// Enum for blood types
enum BloodType {
    A, B, AB, O
}

// Abstract class Person
abstract class Person {
    protected int id;
    protected String name;
    protected int age;
    protected String gender;
    protected String phone;

    public Person(int id, String name, int age, String gender, String phone) {
        this.id = id;
        this.name = name;
        this.age = age;
        this.gender = gender;
        this.phone = phone;
    }

    // Abstract method to get role
    public abstract String getRole();

    // Print basic info
    public void printInfo() {
        System.out.println("ID: " + id);
        System.out.println("Name: " + name);
        System.out.println("Age: " + age);
        System.out.println("Gender: " + gender);
        System.out.println("Phone: " + phone);
        System.out.println("Role: " + getRole());
    }
}

// MedicalRecord class
class MedicalRecord {
    private String description;
    private String date;

    public MedicalRecord(String description, String date) {
        this.description = description;
        this.date = date;
    }

    @Override
    public String toString() {
        return "Date: " + date + ", Description: " + description;
    }
}

// Patient class extending Person
class Patient extends Person {
    private BloodType bloodType;
    private List<MedicalRecord> medicalHistory;

    public Patient(int id, String name, int age, String gender, String phone, BloodType bloodType) {
        super(id, name, age, gender, phone);
        this.bloodType = bloodType;
        this.medicalHistory = new ArrayList<>();
    }

    @Override
    public String getRole() {
        return "Patient";
    }

    public void addMedicalRecord(MedicalRecord record) {
        medicalHistory.add(record);
    }

    public void printMedicalHistory() {
        System.out.println("Medical History of " + name + ":");
        for (MedicalRecord record : medicalHistory) {
            System.out.println(record);
        }
    }

    public BloodType getBloodType() {
        return bloodType;
    }

    public List<MedicalRecord> getMedicalHistory() {
        return medicalHistory;
    }
}
