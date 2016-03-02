# ubiquitous-computing-machine
// my java code
4.3 Sample coding
NymbleServer

import javax.swing.*;
import java.awt.*;
import java.awt.event.*;
import java.io.*;
import java.net.*;
import java.util.*;
import javax.swing.event.*;
import java.sql.*;

class NymbleServer extends JFrame 
{
	 JLabel jl1;
	 JLabel jl2;
	 
	 
	 JButton jb1;
	 JButton jb2;
	 
	 JTextField jt1;
	 JPasswordField jt2;
	 String msg="";
	 
	 
	 Container c;
	 ImageIcon ii;
	 ImageIcon i2;
	 JLabel jl4;
	 JLabel jl6;
	 
	 
	 String str="";
	 String pass="";
	 String path="";
	 String coreaddr="";
	 String core="";
	 String nextcore="";
	 String dest="";
	 String dest1="";
	 File f;
	 File fgs;
	 Vector v = new Vector();

	 NymbleServer()

	 {
		 
		 jl1=new JLabel("Nymble Server Name ");
		 jl2=new JLabel("Server Key ");
		 
		 
		 jb1=new JButton("Send");
		 jb2=new JButton("Reset");
		 
		 jt1=new JTextField(10);
		 jt2=new JPasswordField(10);
		 ii=new ImageIcon("nymbleserver.png");
		 i2=new ImageIcon("nymbleserver1.PNG");
		 jl4=new JLabel(ii);
		 jl6=new JLabel(i2);
		 
		 c = getContentPane();
         c.setLayout(null);
		 c.setBackground(new Color(0,0,120));
		 c.show();
		 c.add(jl1);
		 c.add(jt1);
		 c.add(jl2);
		 c.add(jb1);
		 c.add(jb2);
		 c.add(jl4);
		 c.add(jl6);
		 c.add(jt2);
		 
		    addWindowListener(new java.awt.event.WindowAdapter() {
            public void windowClosing(java.awt.event.WindowEvent evt) {
                exitForm(evt);
            }
        });
		 
		 
		
		 
		
		 jl4.setBounds(30,20,728,68);
		 jl1.setBounds(20,110,200,25);
		 jt1.setBounds(150,110,100,25);
		 jl2.setBounds(50,145,200,25);
		 jt2.setBounds(150,145,100,25);
		 jb1.setBounds(70,235,100,25);
		 jb2.setBounds(180,235,100,25);
		 jl6.setBounds(300,105,485,309);
		 
		 
		 
		 
		 setSize(800,500);
		 setVisible(true);
		 setTitle("Server");
         
		
		

		
		jb1.addActionListener new ActionListener() {

			public void actionPerformed(ActionEvent ae)
			{
				
				
				try {	
      
      if(!jt1.getText().equals("") && !jt2.getText().equals("")){
          
		  JOptionPane.showMessageDialog (null, "Authorised User", "Login Seccess", JOptionPane.INFORMATION_MESSAGE);
		    
		     VerifAdminLogin();
		         
             }
			 else
			 JOptionPane.showMessageDialog((Component) null, "Invalid password. Please try again. ", "Login Error", JOptionPane.INFORMATION_MESSAGE);

			}
			catch(Exception e) { System.out.println(e);
			}

			}
});
	 
		
	
		jb2.addActionListener(new ActionListener() {

			public void actionPerformed(ActionEvent ae)
			{
			jt1.setText("");
			jt2.setText("");
			} 
			});
			

			 
   }
   
    private void exitForm(java.awt.event.WindowEvent evt) {//GEN-FIRST:event_exitForm
        dispose();
    }	

	 public static void main(String a[])

	 {
		 new FileOpen();
	 }
	 
	 void VerifAdminLogin() 
		{
				Connection con=null;
				String url="jdbc:odbc:nymble";
				Statement st=null;
				
			  try
			  {
					
						 String val1=jt1.getText();
						 val1 = val1.trim();
						 String val2 =  (String)jt2.getText();
						 val2 = val2.trim();					
					
					Class.forName("sun.jdbc.odbc.JdbcOdbcDriver");
					
			   		con=DriverManager.getConnection(url);
					
			   		st = con.createStatement();
					
	
				ResultSet rs=st.executeQuery("Select Key from Server where SerName='"+val1+"'");
				
				while(rs.next()){
					String user = rs.getString(1);
					
					boolean b=user.equals(val2);				
				
					if(b)
					{
					
					  new Server().show();
				}
					 else
					{
						JOptionPane.showMessageDialog((Component) null, "Invalid password. Please try again. ", "Login Error", JOptionPane.INFORMATION_MESSAGE);
						jt1.setText("");
						jt2.requestFocus();
					}
					}
			  }
			  catch(SQLException ex)
			   {
			    System.out.println("Unable to access the database");
			   }
			  catch(ClassNotFoundException ex)
			   {
			    System.out.println("Class not found");
			   }
			  catch(Exception ex)
			  {
               System.out.println("Exception raised is:"+ex);
			  }
			  finally {
			  con=null;
			  }
		}

 }






 PseudonymManager
import java.awt.*;
import java.io.*;
import java.util.Vector;

public class PseudonymManager extends javax.swing.JFrame {
     
    
    
    public PseudonymManager() {
        initComponents();
        
               
    }
    
   
    private void initComponents() {
        jPanel1 = new javax.swing.JPanel();
        jLabel1 = new javax.swing.JLabel();
        download = new javax.swing.JButton();
        save = new javax.swing.JButton();
        jLabel2 = new javax.swing.JLabel();
		
        getContentPane().setLayout(null);
		getContentPane().setBackground(new java.awt.Color(104, 174, 254));

        setBackground(new java.awt.Color(0, 204, 204));
        addWindowListener(new java.awt.event.WindowAdapter() {
            public void windowClosing(java.awt.event.WindowEvent evt) {
                exitForm(evt);
            }
        });

        jPanel1.setLayout(null);
		jPanel1.setBackground(new java.awt.Color(104, 174, 254));
        jLabel1.setFont(new java.awt.Font("Arial", 0, 25));
        jLabel1.setText("");
        //jPanel1.add(jLabel1);
        jLabel1.setBounds(200, 10, 480, 40);
		
		
        
        download.setBackground(new java.awt.Color(204, 204, 254));
        download.setFont(new java.awt.Font("Arial", 0, 18));
        download.setText("Start Pseudonym Manager");
        download.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                downloadActionPerformed(evt);
            }
        });

        jPanel1.add(download);
        download.setBounds(200, 100, 320, 50);

        getContentPane().add(jPanel1);
        jPanel1.setBounds(0, 70, 740, 200);

        save.setBackground(new java.awt.Color(204, 174, 254));
        save.setFont(new java.awt.Font("Arial", 0, 18));
        save.setText("Stop Pseudonym Manager");
        save.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                saveActionPerformed(evt);
            }
        });

        getContentPane().add(save);
        save.setBounds(200, 290, 320, 50);
		
		
		

		
       

       
		jLabel2.setFont(new Font("Arial", 0, 25));
        jLabel2.setForeground(new java.awt.Color(222,20, 202));
		jLabel2.setBackground(new java.awt.Color(114, 74, 54));
        jLabel2.setText("Pseudonym Manager");
         getContentPane().add(jLabel2);
        jLabel2.setBounds(250, 30, 270, 40);

        pack();
		setTitle("Nymble_Pseudonym Manager");
		setSize(800,600);
    }	

    private void saveActionPerformed(java.awt.event.ActionEvent evt) {//GEN-FIRST:event_saveActionPerformed
        Runtime r = Runtime.getRuntime();
Process p = null;
String cmd = "../nymble/shutdown.bat";
try {
p = r.exec(cmd);

p.waitFor(); 

} catch (Exception e) {
System.out.println("error executing " + cmd);
}
System.out.println(cmd + " returned " + p.exitValue());
        
        
    }
    private void downloadActionPerformed(java.awt.event.ActionEvent evt) {//GEN-FIRST:event_downloadActionPerformed
        
               
		Runtime r = Runtime.getRuntime();
Process p = null;
String cmd = "../nymble/startup.bat";
try {
p = r.exec(cmd);

p.waitFor(); 

} catch (Exception e) {
System.out.println("error executing " + cmd);
}
System.out.println(cmd + " returned " + p.exitValue());
        
        
    }
	 private void browserActionPerformed(java.awt.event.ActionEvent evt) {//GEN-FIRST:event_downloadActionPerformed
        
       
try {



} catch (Exception e) {
System.out.println("error executing browser " + evt);
}    
    }
	
	
	
    private void exitForm(java.awt.event.WindowEvent evt) {//GEN-FIRST:event_exitForm
        System.exit(0);
    }
    
    
    public static void main(String args[]) {
        new PseudonymManager().show();
    }
    
     private javax.swing.JButton download;
    private javax.swing.JLabel jLabel1;
    private javax.swing.JLabel jLabel2;
    private javax.swing.JPanel jPanel1;
    private javax.swing.JButton save;
}

PasswordGenerator
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
import java.util.Random;



public class PasswordGenerator {


char numberChars[] = "0123456789".toCharArray();


char lowerChars[] = "abcdefghijklmnopqrstuvwxyz".toCharArray();


char upperChars[] = "ABCDEFGHIJKLMNOPQRSTUVWXYZ".toCharArray();


char otherSpecialChars[] = "`~!@#$%^&*()-_=+[{]}\\|;:'\",<.>/?".toCharArray();


List <Integer>listForLengthOfPassword = new ArrayList<Integer>();


Random random = new Random();


List <Character>finalpasswordList;


public PasswordGenerator(){

listForLengthOfPassword.add(1);
listForLengthOfPassword.add(2);
listForLengthOfPassword.add(2);
listForLengthOfPassword.add(3);
}


public String getPassword(){

Collections.shuffle(listForLengthOfPassword);
finalpasswordList = new ArrayList<Character>();

for(int t=0;t<listForLengthOfPassword.size();t++){

int numberOfCharPerArray = listForLengthOfPassword.get(t);
for(int z=0;z<numberOfCharPerArray;z++){

if(t == 0){

finalpasswordList.add(numberChars[random.nextInt(10)]);
}else if(t == 1){

finalpasswordList.add(lowerChars[random.nextInt(26)]);
}else if(t == 2){

finalpasswordList.add(upperChars[random.nextInt(26)]);
}


else if(t == 3){

finalpasswordList.add(otherSpecialChars[random.nextInt(32)]);
}

}//end for

}//end for

String password = new String();
Collections.shuffle(finalpasswordList);
for(int s=0;s<finalpasswordList.size();s++){

password += finalpasswordList.get(s);
}
return password;
}


public static void main(String args[]){

PasswordGenerator passwordGenerator = new PasswordGenerator();

//for(int u=0; u<1000; u++)
{

System.out.println(passwordGenerator.getPassword());
}
}

}

Login
import java.rmi.*;
import java.rmi.server.*;
import java.net.*;
import java.io.*;
import javax.swing.*;
import java.awt.event.*;
import java.lang.*;
import java.awt.*;
import javax.swing.filechooser.FileSystemView;
import java.util.StringTokenizer;
import java.net.InetAddress;
import java.rmi.Naming;
import java.util.Date;
import java.util.Vector;
import java.util.Random;
public class Login extends javax.swing.JFrame 
{
	    RMISIntf ref;
	   JOptionPane op;
	    Vector v= new Vector(2);
	    String sss=null;
		static String username;

    /** Creates new form Login */

	    public Login()
	 {
	        initComponents();
    	 }
  
  	  private void initComponents() 
		{
		
        	         jPan = new javax.swing.JPanel();
	         jLabel1 = new javax.swing.JLabel();
	        user = new javax.swing.JTextField();
	        jLabel2 = new javax.swing.JLabel();
	        submit = new javax.swing.JButton();
	        reset = new javax.swing.JButton();
	        exit = new javax.swing.JButton();
	        pass = new javax.swing.JPasswordField();
	        jLabel3 = new javax.swing.JLabel();
	       op=new JOptionPane();
	       getContentPane().setLayout(null);
	
       	       jPanel1 = new javax.swing.JPanel();
	       listres = new javax.swing.JList();
	        jLab = new javax.swing.JLabel();
	        download = new javax.swing.JButton();
	        resArea = new TextArea();
	        save = new javax.swing.JButton();

	        getContentPane().setLayout(null);
			getContentPane().setBackground(new Color(200,40,50));

	        addWindowListener(new java.awt.event.WindowAdapter() 
		{
		            public void windowClosing(java.awt.event.WindowEvent evt) 
			{
	
                		exitForm(evt);
	
            			}
		  });

	        jPan.setLayout(null);

	        jPan.setBackground(new java.awt.Color(200, 113, 181));
	        jPan.setBorder(new javax.swing.border.EtchedBorder());
	        jLab.setFont(new java.awt.Font("Arial", 0, 14));
	        jLab.setText("User ID:");
	        jPan.add(jLab);
	        jLab.setBounds(40, 40, 90, 30);

	        jPan.add(user);
	        user.setBounds(140, 40, 100, 30);

	        jLabel2.setFont(new java.awt.Font("Arial", 0, 14));
	        jLabel2.setText("Password:");
	        jPan.add(jLabel2);
	        jLabel2.setBounds(40, 90, 90, 30);

	        submit.setBackground(new java.awt.Color(204, 204, 255));
	        submit.setFont(new java.awt.Font("Arial", 0, 14));
	        submit.setForeground(new java.awt.Color(0, 0, 153));
	        submit.setText("Submit");

	        submit.addActionListener(new java.awt.event.ActionListener() 
		{
		        public void actionPerformed(java.awt.event.ActionEvent evt)
			 {
			                submitActionPerformed(evt);
           			 }
        		});

	        jPan.add(submit);
	        submit.setBounds(20, 150, 80, 27);

	        reset.setBackground(new java.awt.Color(204, 204, 255));
	        reset.setFont(new java.awt.Font("Arial", 0, 14));
	        reset.setForeground(new java.awt.Color(0, 0, 153));
	        reset.setLabel("Reset");

	        reset.addActionListener(new java.awt.event.ActionListener()
		 {
		            public void actionPerformed(java.awt.event.ActionEvent evt) 
			{
		                resetActionPerformed(evt);
            			}
        		});

	        jPan.add(reset);
	        reset.setBounds(120, 150, 80, 27);

	        exit.setBackground(new java.awt.Color(204, 204, 255));
	        exit.setFont(new java.awt.Font("Arial", 0, 14));
	        exit.setForeground(new java.awt.Color(0, 0, 153));
	        exit.setLabel("Exit");
	        exit.addActionListener(new java.awt.event.ActionListener() 
		{
	            		public void actionPerformed(java.awt.event.ActionEvent evt) 
				{
			                exitActionPerformed(evt);
           				 }
		  });

	        jPan.add(exit);
	        exit.setBounds(220, 150, 70, 27);

	        jPan.add(pass);
	        pass.setBounds(140, 91, 100, 30);

	        getContentPane().add(jPan);
	        jPan.setBounds(250, 140, 320, 200);

	        jLabel3.setFont(new java.awt.Font("Arial", 0, 24));
	        jLabel3.setForeground(new java.awt.Color(255, 255, 255));
	        jLabel3.setText("Nymble: Blocking Misbehaving Users in Anonymizing Networks");
			jLabel3.setFont(new java.awt.Font("Arial", 0, 18));
	        getContentPane().add(jLabel3);
	        jLabel3.setBounds(100, 30, 570, 30);
		

	        pack();

	        jPanel1.setLayout(null);

	        jPanel1.setBorder(new javax.swing.border.EtchedBorder());
	        listres.setBorder(new javax.swing.border.SoftBevelBorder(javax.swing.border.BevelBorder.LOWERED));
	        jPanel1.add(listres);
	        listres.setBounds(10, 60, 150, 220);

	        jLabel1.setFont(new java.awt.Font("Arial", 0, 15));
	        jLabel1.setText("Resources Available:");
	        jPanel1.add(jLabel1);
	        jLabel1.setBounds(10, 10, 180, 40);

	        download.setBackground(new java.awt.Color(204, 204, 254));
	        download.setFont(new java.awt.Font("Arial", 0, 15));
	        download.setText("Access File..");
	
	        download.addActionListener(new java.awt.event.ActionListener() 
		{
		            public void actionPerformed(java.awt.event.ActionEvent evt) 
			{
			                downloadActionPerformed(evt);
            			}
		   });

	        jPanel1.add(download);
	        download.setBounds(180, 60, 140, 27);
	
	        getContentPane().add(jPanel1);
	        jPanel1.setBounds(20, 70, 340, 300);
	
	
	        getContentPane().add(resArea);
	        resArea.setBounds(400, 90, 240, 250);

	        save.setBackground(new java.awt.Color(204, 204, 254));
	        save.setFont(new java.awt.Font("Arial", 0, 15));
	        save.setText("Save");
	        save.addActionListener(new java.awt.event.ActionListener() 
		{
		            public void actionPerformed(java.awt.event.ActionEvent evt) 
			{

		                saveActionPerformed(evt);
				
            			}
        		});

	        getContentPane().add(save);
	        save.setBounds(470, 370, 70, 27);
	       resArea.setVisible(false);
	       save.setVisible(false);
       
	        jPanel1.setVisible(false);
	        jPanel1.setBackground(new java.awt.Color(0, 204, 204));
	
    	}
	//GEN-END:initComponents

	    private void exitActionPerformed(java.awt.event.ActionEvent evt)
		 {
		//GEN-FIRST:event_exitActionPerformed
	
		          System.exit(0);
		    }


	    private void resetActionPerformed(java.awt.event.ActionEvent evt) 
		{
		//GEN-FIRST:event_resetActionPerformed

		        user.setText("");
		        pass.setText("");
		    }

    private void submitActionPerformed(java.awt.event.ActionEvent evt) 
	{
	try
	{

		ref= (RMISIntf)Naming.lookup("rmi://"+"192.168.1.55"+"/RMIServer");
		//System.out.println(ref.res("sdsd","dsa"));


if(user.getText().trim().equals(""))
			{
			   op.showConfirmDialog(this,"Enter The User Name","Alert",JOptionPane.DEFAULT_OPTION,JOptionPane.ERROR_MESSAGE);
			   user.grabFocus();
			}
	else
	{
			   if(pass.getText().trim().equals(""))
			   	{
	                            		 op.showConfirmDialog(this,"Enter The PassWord","Alert",JOptionPane.DEFAULT_OPTION,JOptionPane.ERROR_MESSAGE);
				 pass.grabFocus();
				 }
			else
			{
				InetAddress Address = InetAddress.getLocalHost();	
				String c =Address.getHostAddress();
				ref= (RMISIntf)Naming.lookup("rmi://"+"192.168.1.55"+"/RMIServer");
					String ss=ref.CliDet(user.getText(),pass.getText(),c);
					if(ss.equals("notok"))
					{
					op.showConfirmDialog(this,"UnAuthorised User","Alert",JOptionPane.DEFAULT_OPTION,JOptionPane.ERROR_MESSAGE);
					user.grabFocus();
					}

else
{

username=user.getText();
String key=(String)JOptionPane.showInputDialog(this,"Enter your Key:");
ref=(RMISIntf)Naming.lookup("rmi://"+"192.168.1.55"+"/RMIServer");
String status=ref.CliDet_key(user.getText(),key);
	if(status.equals("ok"))
	{
	
	username=user.getText();	
	//getContentPane().remove(jPan);//.visible(false);
	jPan.setVisible(false);
	jPanel1.setVisible(true);
	resArea.setVisible(true);
	save.setVisible(true);
	StringTokenizer token=new StringTokenizer(ss,";");
	while(token.hasMoreTokens())
	{
	String nextToken = token.nextToken();
	v.addElement(nextToken);
	System.out.println(nextToken);
	}
	listres.setListData(v);	
	}///inner if
	
	
	else
	{
	op.showConfirmDialog(this,"UnAuthorised User","Alert",JOptionPane.DEFAULT_OPTION,JOptionPane.ERROR_MESSAGE);
					user.grabFocus();
	}
}

}
		
		}
	
	}catch(Exception e){System.out.println(e);}



    }

    private void downloadActionPerformed(java.awt.event.ActionEvent evt) 
		{
		        

	               sss=(String)listres.getSelectedValue();
	               System.out.println(sss);
		int ch=0;
		try{
			InetAddress Address = InetAddress.getLocalHost();	
			String c =Address.getHostAddress();	
			/////////////////////////////////////////////////////

			String aa[]=new String[4];
			ref= (RMISIntf)Naming.lookup("rmi://"+"192.168.1.55"+"/RMIServer");
		/////////////////////////
		String chh=ref.checkipp(c,sss);
		StringTokenizer st=new StringTokenizer(chh,";");
		String ipp=null;
		String opp=null;
		//while(st.hasMoreTokens()) {
	
			 ipp=st.nextToken();
			System.out.println(ipp+"hai");

			opp=st.nextToken();
			System.out.println(opp);
		
			//}			
			

		String optiontest="null";	
			if(ipp.equals("ok")||opp.equals("true"))
			{
			optiontest="true";
						
			String a=(String)JOptionPane.showInputDialog(this,"Enter your password:");
				aa[0]=a;
				a=(String)JOptionPane.showInputDialog(this,"Enter your  correct password:");
				aa[1]=a;
				a=(String)JOptionPane.showInputDialog(this,"Enter correct password:");	
				aa[2]=a;
				System.out.println(aa[0]+aa[1]);
				aa[3]=new Date().toString();
			ref.store(aa,c,username,sss);
			JOptionPane.showMessageDialog (null, "IP Blocked & you are Misbehaving User &you Can't Access Nymble web Page & Cant downlod the file", "you Can't Access Nymble web Page", JOptionPane.ERROR_MESSAGE);
			}
/////////change
			String ssss=ref.res(sss,c,optiontest);
			/********File ss=ref.res(sss,c,);
				
                	        //File file = new File(ss);
	                	FileInputStream in = new FileInputStream(ss);
	                	int i = in.available();
			char st[]=new char[i];
			int j =0;                 			
			while((ch=in.read())!=-1) 
				{
					st[j] = (char) ch;
					j++;
				}
		                   String str=new String(st);
			   resArea.setText(str);
					***********/		
				System.out.println("new	"+ssss);
			    resArea.setText(ssss);
			Logged1 l1=new Logged1();
		    l1.show();


  		} catch(Exception e) 
			{
			 System.out.println(e);      
			}
        
    }


    private void saveActionPerformed(java.awt.event.ActionEvent evt) 
		{
			//GEN-FIRST:event_saveActionPerformed

		try {
			FileDialog fd=new FileDialog(this,"File Store", FileDialog.SAVE);
			fd.setVisible(true);
			String f= fd.getFile();
			fd.setFile(f); // Filename filter
			fd.setDirectory("."); // Current directory
			
			//fd.show();
			FileOutputStream out=new FileOutputStream(f);	
			String s=resArea.getText();
			System.out.println(s);
			byte b[]=s.getBytes();
			out.write(b);
		} catch(Exception e)
			{
			System.out.println(e);
			}
    }
    
    /** Exit the Application */

    private void exitForm(java.awt.event.WindowEvent evt)
	 {
	//GEN-FIRST:event_exitForm
	        System.exit(0);
    	}
    
    /**
     * @param args the command line arguments
     */
    public static void main(String args[]) {
	JFrame jf1=new Login();
	 jf1.setResizable(false);
	 jf1.setSize(680,500);
	 jf1.setTitle("Nymble: User Login");
	jf1.show();


    }
    
    // Variables declaration - do not modify//GEN-BEGIN:variables
    private javax.swing.JButton exit;
    private javax.swing.JLabel jLabel1;
    private javax.swing.JLabel jLabel2;
    private javax.swing.JLabel jLabel3;
    private javax.swing.JPanel jPan;
    private javax.swing.JPasswordField pass;
    private javax.swing.JButton reset;
    private javax.swing.JButton submit;
    private javax.swing.JTextField user;
    private javax.swing.JButton download;
    private javax.swing.JLabel jLab;
    private javax.swing.JPanel jPanel1;
    private javax.swing.JList listres;
    private java.awt.TextArea resArea;
    private javax.swing.JButton save;

    // End of variables declaration//GEN-END:variables
    
}

