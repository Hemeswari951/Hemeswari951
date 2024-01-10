import org.openqa.selenium.*;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.interactions.Action;
import org.openqa.selenium.interactions.Actions;
import org.openqa.selenium.support.ui.Select;

import java.util.List;


public class Senchola
    {
        public static void main(String[] args) throws InterruptedException {
            System.setProperty("webdriver.chrome.driver", "C:\\Selenium_WebDriver\\chromedriver-win64\\chromedriver-win64\\chromedriver.exe");
            WebDriver driver = new ChromeDriver();
            driver.manage().window().maximize();
            driver.get("https://testautomationpractice.blogspot.com/");
            WebElement Name = driver.findElement(By.id("name"));
            Name.sendKeys("Hema");
            WebElement email = driver.findElement(By.id("email"));
            email.sendKeys("Hema@gmail.com");
            WebElement Phone = driver.findElement(By.id("phone"));
            Phone.sendKeys("7458965265");
            WebElement Address = driver.findElement(By.id("textarea"));
            Address.sendKeys("Electronic city");
            //WebElement Gender = driver.findElement(By.id("gender"));
            //driver.findElement(By.id("female")).click();
            driver.findElement(By.xpath("//input[@id='female' and @name='gender' and @type='radio']")).click();
            System.out.println("Radio Button Option 2 Selected");
            driver.findElement(By.xpath("//input[@id='sunday' and @type='checkbox']")).click();
            driver.findElement(By.xpath("//input[@id='monday' and @type='checkbox']")).click();
            driver.findElement(By.xpath("//input[@id='tuesday' and @type='checkbox']")).click();
            driver.findElement(By.xpath("//input[@id='wednesday' and @type='checkbox']")).click();
            driver.findElement(By.xpath("//input[@id='thursday' and @type='checkbox']")).click();
            driver.findElement(By.xpath("//input[@id='friday' and @type='checkbox']")).click();
            driver.findElement(By.xpath("//input[@id='saturday' and @type='checkbox']")).click();
            WebElement Country_DropDown_List = driver.findElement(By.xpath("//select[@id='country']"));
            Select Country_List = new Select(Country_DropDown_List);
            Country_DropDown_List.click();
            Country_List.selectByValue("india");
            System.out.println("Country Selected");
            driver.findElement(By.xpath("//label[contains(text(),'Colors:')]")).click();
            Thread.sleep(3000);

            WebElement Red_Color = driver.findElement(By.xpath("//select//option[@value='red']"));
            WebElement Blue_Color = driver.findElement(By.xpath("//select//option[@value='blue']"));
            WebElement Green_Color = driver.findElement(By.xpath("//select//option[@value='green']"));
            WebElement Yellow_Color = driver.findElement(By.xpath("//select//option[@value='yellow']"));
            WebElement White_Color = driver.findElement(By.xpath("//select//option[@value='white']"));

            Actions action = new Actions(driver);
            Action seriesOfActions = (Action) action.keyDown(Keys.CONTROL)
                    .click(Red_Color)
                    .click(Blue_Color)
                    .click(Green_Color)
                    .click(Yellow_Color)
                    .click(White_Color)
                    .build();
            seriesOfActions.perform();
            Thread.sleep(3000);

            System.out.println("Colors Selected");

            WebElement DateSelect = driver.findElement(By.id("datepicker"));
            DateSelect.clear();
            DateSelect.sendKeys(Keys.ENTER);
            System.out.println("Date Selected");

            driver.findElement(By.xpath("//a[@href='https://demo.opencart.com/']")).click();
            Thread.sleep(3000);
            System.out.println("Open Cart Link Clicked");
            driver.navigate().back();
            Thread.sleep(3000);
            driver.findElement(By.xpath("//a[@href='https://opensource-demo.orangehrmlive.com/web/index.php/auth/login']")).click();
            Thread.sleep(3000);
            System.out.println("Orange HRM Link Clicked");
            driver.navigate().back();
            Thread.sleep(3000);
            driver.findElement(By.xpath("//a[@href='https://testautomationpractice.blogspot.com/feeds/posts/default']")).click();
            Thread.sleep(3000);
            System.out.println("Posts Atom Link Clicked");
            String winHandleBefore = driver.getWindowHandle();
            for (String winHandle : driver.getWindowHandles()) {
                driver.switchTo().window(winHandle);
            }
            for (String handle1 : driver.getWindowHandles()) {
                driver.switchTo().window(handle1);
            }
            driver.close();
            Thread.sleep(3000);
            driver.switchTo().window(winHandleBefore);
            //driver.switchTo().newWindow(WindowType.valueOf("testautomationpractice"));
            //driver.getWindowHandle();
            //String New_Tab_Title = driver.getTitle();
            //System.out.println("New_Tab_Title "+New_Tab_Title);
            //if(New_Tab_Title.equalsIgnoreCase("testautomationpractice"))
            //{
            //System.out.println("inside If");
            //driver.getWindowHandle();
            System.out.println("Switched To Active Element");
            System.out.println("New Tab Closed");

            WebElement Book_Web_Table = driver.findElement(By.xpath("//table[@name='BookTable']"));
            List<WebElement> rows = Book_Web_Table.findElements(By.xpath(".//tr"));
            for (WebElement row : rows) {
                List<WebElement> cells = row.findElements(By.xpath(".//td"));
                for (WebElement cell : cells) {
                    System.out.println("Contents Of Book WebTable from " + " Row " + rows.indexOf(row) + " Column " + cells.indexOf(cell) + " is : " + cell.getText());
                }
            }

            //Fetch And Print Values From Pagination WebTable
            WebElement Pagination_Web_Table = driver.findElement(By.xpath("//table[@id='productTable']"));
            List<WebElement> Pagination_Web_Table_Rows = Pagination_Web_Table.findElements(By.xpath(".//tr"));
            for (WebElement row : Pagination_Web_Table_Rows) {
                List<WebElement> Pagination_Web_Table_Cells = row.findElements(By.xpath(".//td"));
                for (WebElement cell : Pagination_Web_Table_Cells) {
                    System.out.println("Contents Of Pagination WebTable from " + " Row " + Pagination_Web_Table_Rows.indexOf(row) + " Column " + Pagination_Web_Table_Cells.indexOf(cell) + " is : " + cell.getText());
                }
            }

            WebElement Wiki_Tab = driver.findElement(By.xpath("//*[@class='wikipedia-search-input']"));
            Wiki_Tab.sendKeys("spiderman");
            Wiki_Tab.sendKeys(Keys.ENTER);
            System.out.println("Wiki_Tab Selected");
            WebElement Button = driver.findElement(By.xpath("//button[@onclick='myFunction()']"));
            Button.sendKeys(Keys.ENTER);
            Thread.sleep(3000);
            System.out.println("New Browser Window Clicked");
            String winHandleBefore1 = driver.getWindowHandle();
            for (String winHandle : driver.getWindowHandles()) {
                driver.switchTo().window(winHandle);
            }
            for (String handle1 : driver.getWindowHandles()) {
                driver.switchTo().window(handle1);
            }
            Thread.sleep(3000);
            driver.switchTo().window(winHandleBefore1);
            // driver.navigate().back();
            WebElement Button1 = driver.findElement(By.xpath("//button[@onclick='myFunctionAlert()']"));
            Button1.sendKeys(Keys.ENTER);
            Thread.sleep(3000);
            driver.switchTo().alert().accept();
            System.out.println("Alert Window Clicked");
            WebElement Button2 = driver.findElement(By.xpath("//button[@onclick='myFunctionConfirm()']"));
            Button2.sendKeys(Keys.ENTER);
            Thread.sleep(3000);
            driver.switchTo().alert().accept();
            System.out.println("conformation box Window Clicked");
            WebElement Button3 = driver.findElement(By.xpath("//button[@onclick='myFunctionPrompt()']"));
            Button3.click();
            Thread.sleep(3000);
            Alert alert = driver.switchTo().alert();
            alert.sendKeys("Hema");
            alert.accept();
            System.out.println("Prompt box Window Clicked");
            Thread.sleep(3000);

//Thread.sleep(5000);
//
            driver.findElement(By.xpath("//input[@id='field1']")).click();
            driver.findElement(By.xpath("//input[@id='field1']")).clear();
            System.out.println("Value Cleared In Field 1");
            driver.findElement(By.xpath("//input[@id='field1']")).sendKeys("Welcome");
            System.out.println("Value Entered In Field 1");
            driver.findElement(By.xpath("//input[@id='field2']")).click();
            driver.findElement(By.xpath("//input[@id='field2']")).clear();
            driver.findElement(By.xpath("//input[@id='field2']")).sendKeys("Home");
            System.out.println("Value Entered In Field 2");

            Thread.sleep(3000);
            Actions act = new Actions(driver);
            WebElement copyText = driver.findElement(By.xpath("//button[@ondblclick='myFunction1()']"));
            act.doubleClick(copyText).perform();
            System.out.println("Double Click action performed");
            Thread.sleep(3000);

            WebElement draggable = driver.findElement(By.xpath("//div[@id='draggable']"));
            WebElement droppable = driver.findElement(By.xpath("//div[@id='droppable']"));
            Actions builder = new Actions(driver);
//Building a drag and drop action
            Action dragAndDrop = builder.clickAndHold(draggable)
                    .moveToElement(droppable)
                    .release(droppable)
                    .build();
//Performing the drag and drop action
            dragAndDrop.perform();
            System.out.println("Drag and Drop action performed");

            WebElement slidder = driver.findElement(By.xpath("//div[@id='slider']"));
            Actions move = new Actions(driver);
            move.moveToElement(slidder).clickAndHold().moveByOffset(0, -25).release().perform();
            System.out.println("Slide action performed");
            driver.switchTo().frame(0);
            WebElement TextField1 = driver.findElement(By.xpath("//input[@id=\"RESULT_TextField-0\"]"));
            TextField1.sendKeys("Hema");
            System.out.println("TextField value entered");
            //driver.switchTo().frame(1);
            //int Radio = driver.findElements(By.tagName("iframe")).size();
            //WebElement Radio1=driver.findElement(By.xpath("//label[contains(text(),'Female')]"));
            //Radio1.click();
            //System.out.println("Female value Selected");

            //driver.findElement(By.xpath("//input[@type='radio' and @name='RESULT_RadioButton-1' and @class='multiple_choice' and @id='RESULT_RadioButton-1_1']")).click();
            WebElement Radio_Option = driver.findElement(By.xpath("//input[@type='radio' and @name='RESULT_RadioButton-1' and @class='multiple_choice' and @id='RESULT_RadioButton-1_1']"));
            JavascriptExecutor Executor = (JavascriptExecutor) driver;
            Executor.executeScript("arguments[0].click();", Radio_Option);
            System.out.println("Female Radio Option Selected");

            WebElement DateSelect1 = driver.findElement(By.xpath("//input[@id='RESULT_TextField-2']"));
            DateSelect1.click();
            DateSelect1.sendKeys("10/20/1992");
            System.out.println("DOB Selected");

            WebElement Job_DropDown_List = driver.findElement(By.xpath("//select[@id='RESULT_RadioButton-3']"));
            Job_DropDown_List.click();
            Select Job_List = new Select(Job_DropDown_List);
            Job_DropDown_List.click();
            Job_List.selectByVisibleText("QA Engineer");
            System.out.println("Job Selected");
            Thread.sleep(4000);


            //WebElement Resize1  = driver.findElement(By.xpath("//div[@id='resizable']"));
            //  Actions Resize = new Actions(driver);
            //Resize.moveToElement(Resize1).clickAndHold().moveByOffset(100,150).release().perform();
            //   Resize1.click();
            //   Resize.clickAndHold(Resize1).moveByOffset(100,150).perform();

            WebElement Submit = driver.findElement(By.xpath("//input[@name='Submit']"));
            Submit.click();
            System.out.println("Submit Clicked");
            Thread.sleep(5000);
            //scrolldown1(0, 1550);

            //JavascriptExecutor js = null;
            JavascriptExecutor Window_Scroll_Down = (JavascriptExecutor) driver;
            Window_Scroll_Down.executeScript("window.scrolldown(0,1550)", "");
            System.out.println("Window Scroll Down - Success");

            //Resize_Executor.executeScript("document.getElementById('resizable').style.width = '300px';"
                   // + " document.getElementById('resizable').style.height = '300px';");
            JavascriptExecutor Resize_Executor = (JavascriptExecutor) driver;
            //WebElement Resize = driver.findElement(By.xpath("//div[@id='resizable']"));
            //Resize_Executor.executeScript("arguments[0].click();", Resize);
            Resize_Executor.executeScript("document.getElementById('resizable').style.width = '300px';"
                    + " document.getElementById('resizable').style.height = '300px';");
            System.out.println("Resize Selected");

            Thread.sleep(3000);

            //  WebElement resizerBox=driver.findElement(By.xpath("//div[@id='resizable']"));
            // WebElement resizer=driver.findElement(By.xpath("//div[@class='ui-resizable-handle ui-resizable-se ui-icon ui-icon-gripsmall-diagonal-se']"));
            //   Actions act1 = new Actions(driver);
            //   act.clickAndHold(resizer).moveToElement(resizerBox, 470, 162).perform();
            //  Thread.sleep(4000);
            //  driver.close();


            // WebElement resizableElement = driver.findElement(By.id(" //*[@id='resizable']"));
            // WebElement resizableElement = driver.findElement(By.cssSelector("#resizable"));


            // Create Actions class instance
            // Actions actions = new Actions(driver);

            // Resize the element by moving it
            // actions.clickAndHold(resizableElement).moveByOffset(100, 100).release().perform();
            //System.out.println("Resize Action Performed");

            //   WebElement Resize1  = driver.findElement(By.xpath("//div[@class='ui-widget-content ui-resizable']"));
            // driver .switchTo().frame(4);
            //Dimension newSize = new Dimension(222, 155);
            //driver.manage().window().setSize(newSize);
            //System.out.println("Resize Action Performed");

        }
    }
