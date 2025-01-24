![image](https://github.com/user-attachments/assets/d924111a-0127-40bb-a46b-9738c35cd1cd)
### Mock API Documentation: Google Classroom API

* This is the mock documentation snippet (for Google Classroom) mentioned in the Chapter 5 scenario.
* It is provided to learners during the lab to simulate working with API constraints and to teach them how to interpret documentation for real-world implementation challenges. 
---

#### **Endpoint: Create Assignment**
- **URL**: `https://api.googleclassroom.com/v1/assignments`
- **Method**: POST

**Request Parameters**:
| Parameter       | Type     | Description                                               |
|-----------------|----------|-----------------------------------------------------------|
| `title`         | String   | The title of the assignment.                              |
| `description`   | String   | The detailed description of the assignment.               |
| `attachments`   | Array    | A list of file URLs to be attached to the assignment.     |
| `dueDate`       | Date     | The due date for the assignment in `YYYY-MM-DD` format.   |
| `courseId`      | String   | The unique identifier of the course.                     |

**Example Request**:
```json
POST https://api.googleclassroom.com/v1/assignments
{
  "title": "Midterm Essay",
  "description": "Submit a 5-page essay on the topic provided in class.",
  "attachments": [
    "https://example.com/files/essay-rubric.pdf",
    "https://example.com/files/example-essay.pdf"
  ],
  "dueDate": "2025-02-15",
  "courseId": "course123"
}
```

**Response**:
| Status Code | Description                                |
|-------------|--------------------------------------------|
| 201 Created | Assignment successfully created.           |
| 400 Bad Request | Invalid input or missing required parameters. |
| 403 Forbidden | Unauthorized access to the course.       |

---

#### **API Constraint**
- **Attachments Limit**: Assignments can include a maximum of **5 attachments**. Exceeding this limit will result in a **400 Bad Request** error with the message:
  ```
  "Error: Maximum attachment limit of 5 exceeded."
  ```

**Error Response Example**:
```json
{
  "error": "Maximum attachment limit of 5 exceeded."
}
```
