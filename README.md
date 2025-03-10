```mermaid
graph TD
    A[Student (Flutter App)] --> B{Bluetooth Scan};
    A --> C{Fingerprint Verification};
    A --> D{Location Verification};
    B --> E[Verify Bluetooth MAC Address];
    C --> F[Authenticate Fingerprint];
    D --> G[Validate Location];
    E --> H{Is MAC Valid?};
    F --> I{Is Fingerprint Valid?};
    G --> J{Is Location Valid?};
    
    H -->|Yes| K[Proceed to Mark Attendance];
    H -->|No| L[Deny Attendance];
    I -->|Yes| K;
    I -->|No| L;
    J -->|Yes| K;
    J -->|No| L;
    
    K --> M[Generate PDF Report];
    M --> N[Upload Report to Firebase Storage];
    N --> O[Access Report for Admin];
    
    P[Teacher (Web/Flutter App)] --> Q[Bluetooth Scan for Students];
    P --> R[Validate Student Location];
    P --> S[View and Edit Student Details];
    P --> T[View Previous Attendance Records];
    Q --> K;
    R --> J;
    S --> U[Edit Name, Email, MAC Address, Register Number];
    T --> V[Fetch Attendance Data from Firebase];