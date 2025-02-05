import java.awt.*; 
import java.awt.event.*; 
import java.sql.Connection; 
import java.sql.DriverManager; 
import java.sql.PreparedStatement; 
import java.sql.SQLException; 
 
public class StudentOutpassSystem implements ActionListener { 
    private JFrame frame; 
    private JTextField nameField, reasonField, dateField, daysField; 
    private JButton submitButton; 
 
    // JDBC variables 
    private Connection connection; 
    private static final String JDBC_URL = 
"jdbc:mysql://your_database_host:your_database_port/your_database_name"; 
    private static final String USERNAME = "your_username"; 
    private static final String PASSWORD = "your_password"; 
 
    public StudentOutpassSystem() { 
        // Initialize the database connection 
        initializeDatabase(); 
 
        frame = new JFrame("Student Outpass System"); 
        // ... (unchanged code) 
 
     
10  
 
    // Display the window 
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE); 
        frame.pack(); 
        frame.setVisible(true); 
    } 
 
    private void initializeDatabase() { 
        try { 
            // Load the JDBC driver 
            Class.forName("com.mysql.cj.jdbc.Driver"); 
 
            // Establish the database connection 
            connection = DriverManager.getConnection(JDBC_URL, USERNAME, 
PASSWORD); 
        } catch (ClassNotFoundException | SQLException e) { 
            e.printStackTrace(); 
            JOptionPane.showMessageDialog(frame, "Error connecting to the 
database."); 
            System.exit(1); 
        } 
    } 
 
    public void actionPerformed(ActionEvent e) { 
        if (e.getSource() == submitButton) { 
            String name = nameField.getText(); 
            String reason = reasonField.getText(); 
            String date = dateField.getText(); 
            String days = daysField.getText(); 
 
11  
 
            // Store the outpass details in the database 
            storeOutpassRequest(name, reason, date, days); 
 
            // Prompt for approval/denial 
            approveOrDenyRequest(name); 
        } 
    } 
 
    private void storeOutpassRequest(String name, String reason, String date, 
String days) { 
        try { 
            // Prepare the SQL statement 
            String sql = "INSERT INTO outpass_requests (name, reason, date, days) 
VALUES (?, ?, ?, ?)"; 
            PreparedStatement preparedStatement = 
connection.prepareStatement(sql); 
 
            // Set values for the parameters 
            preparedStatement.setString(1, name); 
            preparedStatement.setString(2, reason); 
            preparedStatement.setString(3, date); 
            preparedStatement.setString(4, days); 
 
            // Execute the SQL statement 
            preparedStatement.executeUpdate(); 
 
            // Close the statement 
            preparedStatement.close(); 
     
12  
 
    } catch (SQLException e) { 
            e.printStackTrace(); 
            JOptionPane.showMessageDialog(frame, "Error storing outpass request 
in the database."); 
        } 
    } 
 
    // ... (unchanged code for approveOrDenyRequest, approveRequest, 
denyRequest) 
 
    public static void main(String[] args) { 
        new StudentOutpassSystem(); 
    } 
} 
