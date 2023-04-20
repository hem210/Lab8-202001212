# Lab8-202001212

## IT314 - Software Engineering<br />
## Lab 7 - Software Testing<br />
202001212<br />
Hemang Joshi<br />


### 1: Create a new Eclipse project, and within the project create a package.<br />

![image](https://user-images.githubusercontent.com/75677231/233315006-e828a366-684e-4085-9744-b0a95993b17f.png)

### 2: Create a class for a Boa. Here’s the code:<br />
```
// represents a boa constrictor
public class Boa {
    private String name;
    private int length; // the length of the boa, in feet
    private String favoriteFood;
    public Boa (String name, int length, String favoriteFood){
        this.name = name;
        this.length = length;
        this.favoriteFood = favoriteFood;
    }
    // returns true if this boa constrictor is healthy
    public boolean isHealthy(){
        return this.favoriteFood.equals("granola bars");
    }
    // returns true if the length of this boa constrictor is
    // less than the given cage length
    public boolean fitsInCage(int cageLength){
        return this.length < cageLength;
    }
}
```

### 3: Follow the instructions in the JUnit tutorial in the section “Creating a JUnit Test Case in Eclipse”. You’ll be creating a test case for the class Boa. When you’re asked to select test method stubs, select both isHealthy() and fitsInCage(int). <br />
```
import org.junit.Test;
import static org.junit.Assert.*;

public class BoaTest {
    
    @Test
    public void testIsHealthy() {
        Boa boa1 = new Boa("Sneaky", 6, "granola bars");
        assertTrue(boa1.isHealthy());
        
        Boa boa2 = new Boa("Slithery", 8, "burger");
        assertFalse(boa2.isHealthy());
    }
    
    @Test
    public void testFitsInCage() {
        Boa boa1 = new Boa("Slinky", 5, "mice");
        assertTrue(boa1.fitsInCage(5));
        assertFalse(boa1.fitsInCage(3));
        
        Boa boa2 = new Boa("Curly", 10, "rabbits");
        assertTrue(boa2.fitsInCage(12));
        assertFalse(boa2.fitsInCage(9));
    }
}
```
The above code shows two test cases that I created for the Boa class.
In the first test case, the isHealthy function is getting tested. The output of the testcase would be true for the first object and false for the second object.

In the second test case, the testFitsinCage function is getting tested. The first Boa will fit in a cage of length 5 but not 3. The second Boa will fit in a cage of length 12 but not 9.

### 4: Modify the setUp() method so that it creates a couple of Boa objects, as follows: <br />

import org.junit.Before;
import org.junit.Test;
import static org.junit.Assert.*;

public class BoaTest {
    
    private Boa jen;
    private Boa ken;
    
    @Before
    public void setUp() throws Exception {
        jen = new Boa("Jennifer", 2, "grapes");
        ken = new Boa("Kenneth", 3, "granola bars");
    }
    
    @Test
    public void testIsHealthy() {
        assertTrue(jen.isHealthy());
        assertTrue(ken.isHealthy());
    }
    
    @Test
    public void testFitsInCage() {
        assertTrue(jen.fitsInCage(3));
        assertFalse(ken.fitsInCage(2));
    }
}

### 5: JUnit also provided stubs for two test methods, each annotated with @Test. Work on the testIsHealthy() method first. Likewise, modify the testFitsInCage() method to test the results of that method.<br />

![image](https://user-images.githubusercontent.com/75677231/233323767-5fa048b4-afc3-4ce2-9b7d-6617a4637fca.png)

```
import org.junit.Before;
import org.junit.Test;
import static org.junit.Assert.*;

public class BoaTest {
    
    private Boa jen;
    private Boa ken;
    
    @Before
    public void setUp() throws Exception {
        jen = new Boa("Jennifer", 2, "grapes");
        ken = new Boa("Kenneth", 3, "granola bars");
    }
    
    @Test
    public void testIsHealthy() {
        assertTrue(jen.isHealthy());
        assertTrue(ken.isHealthy());
    }
}
```
The assertion method is used to check the isHealthy method so that it returns True for both Boa objects.

```
import org.junit.Before;
import org.junit.Test;
import static org.junit.Assert.*;

public class BoaTest {
    
    private Boa jen;
    private Boa ken;
    
    @Before
    public void setUp() throws Exception {
        jen = new Boa("Jennifer", 2, "grapes");
        ken = new Boa("Kenneth", 3, "granola bars");
    }
    
    @Test
    public void testIsHealthy() {
        assertTrue(jen.isHealthy());
        assertTrue(ken.isHealthy());
    }
    
    @Test
    public void testFitsInCage() {
        assertFalse(jen.fitsInCage(1)); // cage length less than boa length
        assertTrue(jen.fitsInCage(2)); // cage length equal to boa length
        assertTrue(jen.fitsInCage(3)); // cage length greater than boa length
        
        assertFalse(ken.fitsInCage(2)); // cage length less than boa length
        assertTrue(ken.fitsInCage(3)); // cage length equal to boa length
        assertTrue(ken.fitsInCage(4)); // cage length greater than boa length
    }
}
```
Added assertions to the testFitsInCage method to check that the fitsInCage method returns the expected results for both jen and ken when the cage length is less than, equal to, and greater than the length of the boa.

Note that the testFitsInCage method is now more robust, as it checks the behavior of the fitsInCage method for different input values.

### 6: Did you get a green bar in the JUnit pane? If you got a red bar, use the output in the JUnit pane to determine which test(s) failed. Fix your tests, and try running the test case again. <br />

![image](https://user-images.githubusercontent.com/75677231/233325439-10d18444-2c90-4403-be5e-42f07f8a0772.png)

### 7: Add a new method to the Boa class. Add a new test case to the BoaTest class that tests the lengthInInches() method. Make sure you annotate the new test method with @Test. Run your tests. <br />

![image](https://user-images.githubusercontent.com/75677231/233326381-99ac782c-a8dd-4ea8-a96d-4e28ac7e2d11.png)

#### Code for the lengthInInches() method<br />
```
public class Boa {
    private String name;
    private int length; // the length of the boa, in feet
    private String favoriteFood;

    public Boa(String name, int length, String favoriteFood) {
        this.name = name;
        this.length = length;
        this.favoriteFood = favoriteFood;
    }

    // returns true if this boa constrictor is healthy
    public boolean isHealthy() {
        return this.favoriteFood.equals("granola bars");
    }

    // returns true if the length of this boa constrictor is
    // less than the given cage length
    public boolean fitsInCage(int cageLength) {
        return this.length < cageLength;
    }

    // produces the length of the Boa in inches
    public int lengthInInches() {
        return this.length * 12;
    }
}
```
#### Code for the testcases for the lengthInInches() method. <br />
```
import static org.junit.Assert.*;
import org.junit.Before;
import org.junit.Test;

public class BoaTest {
    private Boa jen;
    private Boa ken;

    @Before
    public void setUp() throws Exception {
        jen = new Boa("Jennifer", 2, "grapes");
        ken = new Boa("Kenneth", 3, "granola bars");
    }

    @Test
    public void testIsHealthy() {
        assertFalse(jen.isHealthy());
        assertTrue(ken.isHealthy());
    }

    @Test
    public void testFitsInCage() {
        assertTrue(jen.fitsInCage(24));
        assertFalse(jen.fitsInCage(16));
        assertTrue(ken.fitsInCage(36));
        assertTrue(ken.fitsInCage(24));
        assertFalse(ken.fitsInCage(18));
    }

    @Test
    public void testLengthInInches() {
        assertEquals(24, jen.lengthInInches());
        assertEquals(36, ken.lengthInInches());
    }
}
```
