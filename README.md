# assigment1_triangle
public class Triangle {

    private String checkTriangle(double len1, double len2, double len3){
        if(len1 == len2 && len2 == len3){
            return "Equilateral Triangle";    
        }else if(len1==len2 || len2==len3 || len1==len3){
            return "Isosceles Triangle";
        }else{
            return "Scalene Triangle";
        }
    }
    
    private String checkrTriangle(double len1, double len2, double len3){
        if(Math.pow(len1,2) + Math.pow(len2,2) == Math.pow(len3,2)){
            return "Right Triangle";
        }else{
            return "Not a right triangle";
        }
    }
    
    private String checkForValidValues(double len1, double len2, double len3){
    	if(len1<0 || len2<0 || len3<0){
    		return "Length of any side couldn't be negative.";
    	}else if(len1==0 || len2==0 || len3==0){
    		return "Length of any side couldn't be Zero.";
    	}
    	return "";
    }
    
    private boolean validTriangleValues(double len1, double len2, double len3){
    	if((len1+len2)>len3 && (len2+len3)>len1 && (len1+len3)>len2){
    		return true;	
    	}else{
    		return false;
    	}
    }

    public static void main(String[] s){
    	try{
    		if(s.length==0){
    			System.out.println("Please pass length of all sides of a triangle.");
    			return;
    		}
    		
	        String[] triangleLengthArr = s[0].split(",");
	        
	        if(triangleLengthArr.length<3 || triangleLengthArr.length>3){
    			System.out.println("You need to pass 3 values of sides using the expected separator.");
    			return;
    		}
	        
	        Triangle object = new Triangle();
	        double length1 = 0.0, length2 = 0.0, length3 = 0.0;
	        
	        try{
	        	length1 = Double.parseDouble(triangleLengthArr[0]);
	        	length2 = Double.parseDouble(triangleLengthArr[1]);
	        	length3 = Double.parseDouble(triangleLengthArr[2]);
	        }catch(NumberFormatException e){
	        	System.out.println("All values should be numeric.");
	        	return;
	        }
	        
	        String error = object.checkForValidValues(length1, length2, length3);
	        if(!error.equals("")){
	        	System.out.println(error);
	        	return;
	        }
	        
	        if(!object.validTriangleValues(length1, length2, length3)){
	        	System.out.println("Not a Triangle.");
	        	return;
	        }
	        
	        System.out.println("Length-1: "+triangleLengthArr[0]);
	        System.out.println("Length-2: "+triangleLengthArr[1]);
	        System.out.println("Length-3: "+triangleLengthArr[2]);
	        
	        String triangleType = object.checkTriangle(length1, length2, length3);
	        String trianglerType = object.checkrTriangle(length1, length2, length3);
	
	        System.out.println(triangleType);
	        System.out.println(trianglerType);
    	}catch(Exception e){
    		System.out.println(e.toString());
    	}
    }
}
