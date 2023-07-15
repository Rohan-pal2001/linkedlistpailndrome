// Online Java Compiler
// Use this editor to write, compile and run your Java code online

import java.util.*;
public class LinkedList {
    public class Node {
        int data;
        Node next;
        public Node (int data){
            this.data=data;
            this.next=null;
        }
    }
    public static Node head;
    public static Node tail;
    public void addfirst(int data){
        Node newnode= new Node (data);
        if(head==null){
            head=tail=newnode;
            return;
        }
        newnode.next=head;
        head=newnode;
    }
    public void print(){
        if(head==null){
            System.out.println("LL is empty");
            return ;
        }
        Node temp=head;
        while(temp!=null){
            System.out.print(temp.data+" ");
            temp=temp.next;
        }
    }
    public Node findmiddle(Node head){
        Node slow=head;
        Node fast=head;
        while(fast!=null && fast.next!=null){
            slow=slow.next;
            fast=fast.next.next;
        }
        return slow;
    }
    public boolean palindrome(){
        if(head==null || head.next==null){
            return true;
        }
        
        Node mid =findmiddle(head);
        
        Node pre= null;
        Node curr=mid ;
        
        while(curr!=null){
             Node next= curr.next;
            curr.next=pre;
             pre=curr;
            curr=next;
           
        }
        Node right=pre;
        Node left=head;
        while(right!=null){
            if(left.data!=right.data){
                return false;
            }else{
                right=right.next;
                left=left.next;
            }
        }
        return true;
    }
    public static void main(String[] args) {
        LinkedList list = new LinkedList();
        list.addfirst(1);
        list.addfirst(2);
        list.addfirst(3);
        list.addfirst(4);
         list.addfirst(4);
          list.addfirst(3);
           list.addfirst(2);
            list.addfirst(1);
        list.print();
        System.out.println();
       System.out.println(list.palindrome());
       list.print();
    }
}
