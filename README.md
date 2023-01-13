
import java.io.File;
import java.io.FileNotFoundException;
import java.io.IOException;
import java.util.ArrayList;
import java.util.Scanner;

public class LinkedList<T extends Comparable> {
    private Node<T> head=null;
    private Node<T> tail=null;
  
    public Node<T> createNode(T val){
        return new Node<T>(val);
    }

    public void addFront(T val){
        Node<T> newNode=createNode(val);
        if(head!=null) {
    		newNode.next=head;
    		head=newNode;
    		
    	}else {
    		head=newNode;
    		tail=newNode;    }}
    public void addRightAfterHead(T val){
        if(head==null){
            //addFront(val);
            head=createNode(val);
        }
        else{
            Node<T> newNode=createNode(val);//new Node(val);
            newNode.next=head.next;
            head.next=newNode;
        }
    }
    public void display(){
        Node<T> iterator=head;
        while(iterator!=null){
            System.out.println(iterator);
            iterator=iterator.next;

        }
    }
    
    	public void remove(int val) {
    		if(head!=null) {
    			if(head==tail) {
    				if((int)head.val==val)
    				head=null;
    				tail=null;
    			}
    			else {
    				if((int)head.val==val) {
    					Node<T> newNode=head.next;
    					head.next=null;
    					head=newNode;
    					
    				}
    				else {
    					Node<T> iterator1=null;
    					Node<T> iterator2=head;
    					while(iterator2!=null && (int)iterator2.val!=val ) {
    						iterator1=iterator2;
    						iterator2=iterator2.next;
    						
    					}
    					if(iterator2!=null) {
    						if(iterator2==tail) {
    							tail=iterator1;
    							iterator1.next=null;
    						}
    						else {
    							Node <T>iterator3=iterator2.next;
    							iterator2.next=null;
    							iterator1.next=iterator3;
    						}
    					}
    					
    				}	}
    		}	}
    	
    
    public void addLast(T val) {
    	Node<T> newNode=createNode(val);
    	if(head!=null) {
    		tail.next=newNode;
    		tail=newNode;
    		
    	}else {
    		head=newNode;
    		tail=newNode;
    		
    	}
    	
   
    }
    public LinkedList Question1() throws IOException {
    	LinkedList<Integer> s1=new LinkedList();
		File file=new File("Source.txt");
	
		  if(!file.exists()) {

	            file.createNewFile();}
		  	
		  		Scanner s = new Scanner(file);
		  		
		  		while (s.hasNextLine()) {
		  		
		  			
		  			String satir = s.nextLine();
					String[] split = satir.split(",");
					
					for(int i = 0; i < split.length; i++) {
						
						T val2=(T)Integer.valueOf(split[i])		;
							s1.addLast((Integer) val2);		
						
					}
					
		  		}
		  		s.close();
		  		
		  		
		  		ArrayList<Integer> a=new ArrayList();
		  		LinkedList<Integer> s2 =new LinkedList();
		  		Node iterator=s1.head;
		  		while(iterator!=null) {
		  			if(a.contains(iterator.val)) {
		  				iterator=iterator.next;
		  				continue;
		  			}
		  			else {
		  				s2.addLast( (Integer) iterator.val);
		  				a.add((Integer) iterator.val);
		  				iterator=iterator.next;
		  						
		  			}
		  		} 
		  		
		  		
    	return s2;
    }
    public  void Question2() throws IOException  {
    	ArrayList<Integer> a=new ArrayList();
    	
		File file=new File("Search.txt");
		  		Scanner s = new Scanner(file);
		  		
		  		while (s.hasNextLine()) {
		  		
		  			
		  			String satir = s.nextLine();
					String[] split = satir.split(",");
					
					for(int i = 0; i < split.length; i++) {
							T sayi=(T)Integer.valueOf(split[i]);
							a.add((Integer) sayi);
						
					}
					
		  		}
		  		s.close();
		  		LinkedList<Integer> s2 =Question1();
		  		
		  			
		
		  double m=0;
			Node iterator2=s2.head;
			
	  		for(int k:a) {
	  			iterator2=s2.head; 			
	  				if(k==(int)iterator2.val) {
	  					m++;
	  					
	  					continue;
	  					}
	  					
	  				
	  					while((int)iterator2.val!=k ) {
	  						m++;
	  					
	  					
	  					if(iterator2.next!=null) {
	  					iterator2=iterator2.next;}
	  					else {
	  						break;
	  					}
	  					
	  					if((int)iterator2.val==k) {
	  						m++;
	  						break;
	  					}  			
	  			}
	  			
	  		}
	  		System.out.println("Total  number of memory accesses:"+m);
	  		System.out.println("Average number of memory accesses:"+m/a.size());
	}
    
		
    public void Question3() throws IOException {
    	ArrayList<Integer> a=new ArrayList();
		File file=new File("Search.txt");
		
		  	
		  		Scanner s = new Scanner(file);
		  	
		  		while (s.hasNextLine()) {
		  		
		  			
		  			String satir = s.nextLine();
					String[] split = satir.split(",");
					for(int i = 0; i < split.length; i++) {
						T sayi=(T)Integer.valueOf(split[i]);
						a.add((Integer) sayi);
					
				}
					
					
		  		}
		  		s.close();
		  		
		  		
		  		LinkedList s2=Question1();
		
		  	double m=0;
	  		Node iterator2=s2.head;
	  		
	  		for(int k:a){
	  			
	  			iterator2=s2.head;
	  				if((int)iterator2.val==k) {
	  					m++;
                       s2.remove(k);
  						
  						s2.addFront(k);
	  					continue;
	  					}
	  					
	  				else {
	  					while((int)iterator2.val!=k) {
	  					m++;
	  					if(iterator2.next!=null) {
		  					iterator2=iterator2.next;}
		  					else {
		  						break;
		  					}
	  					if((int)iterator2.val==k) {
	  						s2.remove(k);
	  						
	  						s2.addFront(k);
	  						m++;
	  						break;
	  					}
	  				}
	  				
	  			
	  			}
	  			
	  		}
	  		
		
	  		System.out.println("Total  number of memory accesses:"+m);
	  		System.out.println("Average number of memory accesses:"+m/a.size());
    }
    public long second2() throws IOException {		
     	
   	 long start2 = System.currentTimeMillis();	
   	 Question2();
   	return(System.currentTimeMillis() - start2 );

   	     }
     public long second3() throws IOException {
   	     	long start = System.currentTimeMillis();	
   	 Question3();
   	return(System.currentTimeMillis() - start );}
   	   public long second5() throws IOException {
   	     	long start = System.currentTimeMillis();	
   	 	Question5();
   	return (System.currentTimeMillis() - start );}
public long compare1() throws IOException {
	if(second2()>second3()) {
		return second2();
	}
	else {
	return second3();}
	
	
}


 public void Question5() throws IOException {
	
		File file=new File("Search.txt");
		
		ArrayList<Integer> a=new ArrayList();
	
		  if(!file.exists()) {

	            file.createNewFile();}
		  	
		  		Scanner s = new Scanner(file);
		  		
		  		while (s.hasNextLine()) {
		  			
		  			String satir = s.nextLine();
					String[] split = satir.split(",");
					
					for(int i = 0; i < split.length; i++) {						
						T sayi=(T)Integer.valueOf(split[i]);
						a.add((Integer) sayi);
						
					}
					
		  		}
		  		s.close();
		  		
		  		LinkedList<Integer> s2=Question1();
		
		  	double m=0;
	  		Node iterator2=s2.head;
	  		
	  		for(int k:a) {
	  			iterator2=s2.head;
  				if((int)iterator2.val==k) {
  					m++;
                   s2.remove(k);
						s2.addLast(k);
  					continue;
  					}
  					
  				else {
  					while((int)iterator2.val!=k) {
  					m++;
  					if(iterator2.next!=null) {
	  					iterator2=iterator2.next;}
	  					else {
	  						break;
	  					}
  					if((int)iterator2.val==k) {
  						s2.remove(k);
  						
  						s2.addLast(k);
  						m++;
  						break;
  					}
  				}
  				
  			
  				}}
	  		System.out.println("Total  number of memory accesses:"+m);
	  		System.out.println("Average number of memory accesses:"+m/a.size());
	 
 }
 public void compare2() throws IOException {
		if(compare1()>second5()) {
			System.out.println("The others is bigger than second5");
			
		}
		else {
		System.out.println("second5 is bigger than the others");}
		
		
	}

}
