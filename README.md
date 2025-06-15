public void update_data(int sl_no,int new_sl_no,String name){
	DB_connection obj_DB_Connection=new DB_connection();
	Connection connection=obj_DB_Connection.get_connection();
	PreparedStatement ps=null;
try {
	String query="update student set s_id =? , s_name =? where s_id =? ";
	ps=connection.prepareStatement(query);
	ps.setInt(1, new_sl_no);
	ps.setString(2, name);
	ps.setInt(3, sl_no);
	System.out.println(ps);
	ps.executeUpdate();
	}	 
catch (Exception e) {
System.out.println(e);
		}
	}
public void alter_table() {
    DB_connection obj_DB_Connection = new DB_connection();
    Connection connection = obj_DB_Connection.get_connection();
    PreparedStatement ps = null;

    try {
        String query = "ALTER TABLE student ADD age INT";
        ps = connection.prepareStatement(query);
        ps.executeUpdate();
        System.out.println("Column 'age' added successfully to student table.");
    } catch (Exception e) {
        System.out.println("Error (maybe column already exists): " + e);
    }
}
public void describe_table() {
    DB_connection obj_DB_Connection = new DB_connection();
    Connection connection = obj_DB_Connection.get_connection();
    PreparedStatement ps = null;
    ResultSet rs = null;

    try {
        String query = "DESCRIBE student";
        ps = connection.prepareStatement(query);
        rs = ps.executeQuery();

        System.out.println("\nTable Structure (DESCRIBE student):");
        System.out.println("Field\tType\tNull\tKey\tDefault\tExtra");
        while (rs.next()) {
            for (int i = 1; i <= 6; i++) {
                Object value = rs.getObject(i);
                System.out.print(value + "\t");
            }
            System.out.println();
        }
    } catch (Exception e) {
        System.out.println("Error describing table: " + e);
    }
}
public void delete_data(int s_id){
	DB_connection obj_DB_Connection=new DB_connection();
	Connection connection=obj_DB_Connection.get_connection();
	PreparedStatement ps=null;
	try {
		String query="delete from student where s_id=?";
		ps=connection.prepareStatement(query);
		ps.setInt(1, s_id);
		System.out.println(ps);
		ps.executeUpdate();
	} catch (Exception e) {
		System.out.println(e);
	}

}
