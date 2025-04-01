
# Python YAML Use Case  

This project demonstrates how to read, display, and filter student data from a **YAML file** using **Python**. It includes a step-by-step guide for setting up and running the application.

---

## 📌 Features  
✅ Read student data from a **YAML file**  
✅ Display all student information  
✅ Filter students based on **minimum GPA**  
✅ User-friendly command-line interface  

---

## 🛠️ Requirements  
- Python 3.x  
- PyYAML library  

---

## 🔧 Installation  

1. **Install Python (if not installed)**  
   - Download and install Python from [python.org](https://www.python.org/).  
2. **Install PyYAML**  
   ```sh
   pip install pyyaml
   ```
3. **Clone the Repository** (Optional)  
   ```sh
   git clone <repository-url>
   cd <repository-name>
   ```

---

## 📂 Project Structure  
```
├── students.yaml      # YAML file containing student data
├── app.py             # Python script to load and filter students
└── README.md          # Project documentation
```

---

## 📄 Step-by-Step Guide  

### **1️⃣ Create a YAML File (`students.yaml`)**  
```yaml
students:
  - name: Alice
    age: 21
    major: Computer Science
    gpa: 3.8
  - name: Bob
    age: 22
    major: Mathematics
    gpa: 3.5
  - name: Charlie
    age: 20
    major: Physics
    gpa: 3.9
  - name: David
    age: 23
    major: Chemistry
    gpa: 3.2
  - name: Eva
    age: 21
    major: Computer Science
    gpa: 3.7
```

### **2️⃣ Create the Python Script (`app.py`)**  
```python
import yaml

def load_data(file_path):
    """Load data from a YAML file."""
    with open(file_path, 'r') as file:
        data = yaml.safe_load(file)
    return data

def display_students(students):
    """Display all student information."""
    print("\nAll Students:")
    for student in students:
        print(f"Name: {student['name']}, Age: {student['age']}, Major: {student['major']}, GPA: {student['gpa']}")

def filter_students_by_gpa(students, min_gpa):
    """Filter and display students with GPA above the specified minimum."""
    filtered_students = [s for s in students if s['gpa'] >= min_gpa]
    
    print(f"\nStudents with GPA >= {min_gpa}:")
    if filtered_students:
        for student in filtered_students:
            print(f"Name: {student['name']}, Age: {student['age']}, Major: {student['major']}, GPA: {student['gpa']}")
    else:
        print("No students found.")

def main():
    data = load_data('students.yaml')

    if 'students' not in data:
        print("Error: 'students' key not found in the YAML file.")
        return
    
    students = data['students']
    
    display_students(students)

    try:
        min_gpa = float(input("\nEnter minimum GPA to filter students: "))
        filter_students_by_gpa(students, min_gpa)
    except ValueError:
        print("Invalid input! Please enter a numeric GPA value.")

if __name__ == "__main__":
    main()
```

---

## ▶️ Running the Application  

1. Ensure `students.yaml` and `app.py` are in the same directory.  
2. Open a terminal in the project directory and run:  
   ```sh
   python app.py
   ```
3. The program will:  
   - Display all students  
   - Prompt for a minimum GPA  
   - Display students who meet the GPA requirement  

---

## 🔍 Example Output  

```
All Students:
Name: Alice, Age: 21, Major: Computer Science, GPA: 3.8
Name: Bob, Age: 22, Major: Mathematics, GPA: 3.5
Name: Charlie, Age: 20, Major: Physics, GPA: 3.9
Name: David, Age: 23, Major: Chemistry, GPA: 3.2
Name: Eva, Age: 21, Major: Computer Science, GPA: 3.7

Enter minimum GPA to filter students: 3.6

Students with GPA >= 3.6:
Name: Alice, Age: 21, Major: Computer Science, GPA: 3.8
Name: Charlie, Age: 20, Major: Physics, GPA: 3.9
Name: Eva, Age: 21, Major: Computer Science, GPA: 3.7
```

---

## 🎯 Future Enhancements  
🔹 **Sort students** by GPA or Name  
🔹 **Add functionality** to update or delete students  
🔹 **Save filtered results** back to YAML  

