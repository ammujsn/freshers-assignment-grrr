# Assignment – Swachh Bharat

Presented here in this Mandatory README file is the information describing the application for the Swachh Bharat Scheme. This is an innovative application which will make our nation a better and a cleanlier place to live in. Users can freely register themselves in a very simple manner. The information such as the kinds of waste which can be glass, paper, metal can be submitted. The most exciting thing that will attract users to this application is that they can gain coupon points on learning to recycle. This will be beneficial to the user as well as simultaneously cleaning the nation. The users will receive the coupon points immediately. The coupon points are calculated based on the amount of waste deposited in the application. The points and the coupons can be claimed in an instant manner. The economical factor about this application is that it can be accessed by multiple users at once. The application is free to accept different types of waste such as paper, glass, metal, etc. The application is to allow different kinds of waste in a single try. After entering the details such as quantity and type, a detailed report is formatted through the application consisting of the count, type, individual weight as well as the total weight of the waste submitted though the application. The detailed message explaining the amount of coupon points is also generated along with this. The main data attributes include the user, type of the waste submitted by the user, individual weight of the wastage, total weight of the wastage and total number of coupon points that the user earned based on the waste submitted. Java is the programming language to be used to develop this application and maven is used as the build system for compiling and producing the binary. The application produces a JAR file which we can run from the command line by passing necessary arguments. Class path dependencies are also included in order to be able to run the solution of the application. Decoupling the data from the system could be read from a file rather than hard coding within the solution in the application. The Swachh Bharat application can be used by users of all ages and intelligence as it is simple and fun. It is an economical and amusing way of cleaning the nation little by little which will eventually lead to change in the future.

# Coding
public class SwachhGUI extends JFrame implements ActionListener, PrinterInterface
{
UserPanel=myUserPanel=new UserPanel(this);
Random rand=new Random();
public void actionPerformed(ActionEvent e)
{
if(e.getSource().equals(slot1))
{
myUserPanel.itemReceived(1);
}
else if(e.getSource().equals(slot2))
{
myUserPanel.itemReceived(2);
}
else if(e.getSource().equals(slot3))
{
myUserPanel.itemReceived(3);
}
else if(e.getSource().equals(slot4))
{
myUserPanel.itemReceived(4);
}
else if(e.getSource().equals(slot5))
{
myUserPanel.itemReceived(5);
} else if(e.getSource().equals(emptyMachine))
{
slot1.setVisible(true);
slot2.setVisible(true);
slot3.setVisible(true);
slot4.setVisible(true);
slot5.setVisible(true);
slot6.setVisible(true);
coupon.setVisible(true);
emptyMachine.setVisible(false);
output.setText("Machine Cleared");
}
else if(e.getSource().equals(slot6))
{
myUserPanel.itemReceived(rand.nextInt(10));
}
else if(e.getSource().equals(coupon))
{
myUserPanel.printCoupon();
}
}
JButton slot1=new JButton ("Can");
JButton slot2=new JButton ("Bottle");
JButton slot3=new JButton ("Glass Bottle");
JButton slot4=new JButton ("Crate");
JButton slot5=new JButton ("Paper Bag");
JButton slot6=new JButton ("Unknown");
JTextArea output=new JTextArea(10, 50);
JPanel panel=new JPanel();
Font font=new font("Times New Roman", Font.PLAIN, 14);
public SwachhGUI()
{
super();
setSize(600,300);
setResizable(false);
panel.add(slot1);
panel.add(slot2);
panel.add(slot3);
panel.add(slot4);
panel.add(slot5);
panel.add(slot6);
panel.add(emptyMachine);
slot1.addActionListener(this);
slot2.addActionListener(this);
slot3.addActionListener(this);
slot4.addActionListener(this);
slot5.addActionListener(this);
slot6.addActionListener(this);
emptyMachine.addActionListener(this);
emptyMachine.setVisible(false);
panel.add(coupon);
coupon.addActionListener(this);
output.setFont(font);
public Static void main(String [] args) 
{
SwachhGUI myGUI=new SwachhGUI();
myGUI.setVisible(true);
}
public void print(String str)
{
System.out.println(str);
output.setText(str);
}
public class UserPanel
{
DepositItem item=null;
public void itemReceived(int slot)
{
item.classifyItem(slot);
}
public float calculatePercent()
{
return item.calculateWeightPercent();
}
public UserPanel(PrinterInterface printer)
{
super();
item-new DepositItem(printer);
}
public void printCoupon()
{
item.printCoupon();
}
}
public class DepositItem
{
PrinterInterface printer=null;
public void createCouponBasis()
{
theCouponBasis=new CouponBasis();
}
public float calculateWeightPercent()
{
float percentage;
int weight=0;
int maxweight=2500;
weight=thecouponBasis.computeWeight();
percent=(weight*100/maxWeight);

return percentage;
)
public void classifyItem(int slot)
{
DepositItem item=null;
if(slot==1)
{
item=newCan();
}
else if(slot==2)
{
item=newBottle();
}
else if(slot==3)
{
item=newGlassBottle();
}
else if(slot==4)
{
item=newCrate();
}
else if(slot==5)
{
item=newPaperBag();
}
else {
item=new ErrorItem();
}
if(theCouponBasis==null)
{
createCouponBasis();
}
theCouponBasis.addItem(item);
}
public DepositItem(PrinterInterface printer)
{
super();
this.printer=printer;
}
public void printCoupon()
{
String str="";
try
{
str=theCouponBasis.computeSum();
}
catch(Exception e)
{
str="Error! You didn't enter any item";
}
printer.print(str);
theCouponBasis=null;
}
}
public int computeWeight()
{
int totalweight=0;
int weight=0;
for(int i=0; i<myItems.size(); i++)
{
DepositItem item=myItems.get(i);
totalWeight+=item.weight;
}
return totalWeight;
}
public String computeSum()
{
String receipt="";
int bottleCount=0,canCount=0,crateCount=0,paperbagCount=0,glassbottleCount=0;
int totalItems=0;
int sum=0;
for(int i=0; i<myItems.size();i++)
{
DepositItem item=myItems.get(i);
coupon=coupon+item.number+":"+item.getName()+":"+item.value;
switch(item.getName())
{
case "Bottle":
bottleCount++;
break;
case "Glass Bottle":
bottleCount++;
break;
case "Crate":
bottleCount++;
break;
case "Paper Bag":
bottleCount++;
break;
}
sum=sum+item.value;
totalItems=bottleCount+canCount+paperbagCount+glassbottleCount;
coupon=coupon+bottleCount+canCount+paperbagCount+glassbottleCount'
return coupon;
}
}
public class CouponPrinter implements PrinterInterface
{
public void print(String str)
{
System.out.println(str);
}
}
public class ErrorItem extends DepositItem
{
static int size=0;
public ErrorItem()
{
value=0;
weight=0;
}
public String getName()
{
return "Error With Item Inserted";
}
}


