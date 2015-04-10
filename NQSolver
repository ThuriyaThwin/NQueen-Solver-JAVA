import java.util.PriorityQueue;
import java.util.Random;


public class NQSolver {
	
	public PriorityQueue<state> neighbor;
	public state initialState;
	public int N;
	public state currentState;
	public int iteration=0;
	
	public NQSolver(int  N){
		
		this.N=N;
		neighborComparator nc=new neighborComparator();
		neighbor=new PriorityQueue<state>(10,nc);
		buildInitial();
		currentState=new state(N);
		 //make current state equals to initial state
		//at the begining
		currentState.setConfig(initialState.config);;
		currentState.getScore();
		
	}
	public void buildInitial(){
		
		initialState=new state(N);
		
		for(int i=1;i<=N;i++){
			
			Queen q=new Queen(i,i);
			q.setIndex(i);
			q.setLimit(N);
			initialState.config.add(q);
			
		}
	}
	public void findGoal(){
		
		//if score is n, goal found
		while(currentState.Score!=0){
			
			iteration++;
			decideNextCurrentState();
		}
		
		if(currentState.Score==0){
			
			System.out.println("find goal by "+iteration+" iterations");
			
		}
		
	}
	public void decideNextCurrentState(){
		
		makeNeighborSet();
		
		state next=neighbor.poll();
		
		//System.out.println("what is next: "+next+"with score \n"+next.Score);
		
		if(next.Score<currentState.Score){
			//if the neighbor with highest
			//score is better
			System.out.println(next);
			currentState=next;
		
		}else{
			
			Random random = new Random();
			double prob=getProb(currentState,next,iteration);
			//if happens
			if(random.nextDouble()<prob){
				currentState=next;
			}else{
				//do nothing
			}
			
			
		}
		
		this.neighbor.clear();
		
	}
	public void makeNeighborSet(){
		
		int randomN=RandomGenerator(7,3);
		//each time produce 3-7 neighbors and
		//put them into neighbor set
		for(int i=0;i<randomN;i++){
			
			makeNeighbor();	
		}
		
	}
	public void makeNeighbor(){
		
		//derive neighbors from current state
		//produce one neighbor per time
		
		state refer=new state(N);
		refer.setConfig(currentState.config);
		
			
			int randomC=RandomGenerator(25,1);
			
			while(isEmptyCol(randomC)){
				
				randomC=RandomGenerator(25,1);
				
				}
			
			//the queen we intend to move
			Queen temp=findQueenByColumn(randomC);
					
			int randomR=RandomGenerator(25,1);
			
			if(!isOccupied(temp,randomR)){
				
				//System.out.println("move "+temp);
				
				temp.location.setX(randomR);
				refer.removeByIndex(temp.index);
				
				//a new found state
				refer.config.add(temp);
				refer.getScore();
				//System.out.println("to "+temp+" get:");
				//System.out.println(refer);
				
				neighbor.add(refer);
			}
				
			
		
		
	}
	public boolean isEmptyCol(int column){
		
		boolean isEmpty=true;
		for(Queen q:currentState.config){
			
			if(q.location.y==column){
				
				isEmpty=false;
				break;
			
			}
		}
		return isEmpty;
	}
	public Queen findQueenByColumn(int column){
		
		Queen temp=null;
		//get the queen in that column
		for(Queen q:currentState.config){
			
			if(q.location.y==column){
				
				temp=new Queen(q.location.x,q.location.y);
				temp.setIndex(q.index);
				break;
			
			}
		}
		return temp;
		
	}
	public double getProb(state s1, state s2,int iteration){
		//boltzman distribution
		double prob=Math.exp(-((Math.abs(s1.Score-s2.Score)/(Math.pow(0.9, iteration)))));
		//System.out.println(prob);
		return prob;
		
		
	}
	public int RandomGenerator(int  max, int min){
		Random rand = new Random();
		int randomNum = rand.nextInt((max - min) + 1) + min;
		return randomNum;
	}
	public boolean isOccupied(Queen q,int nextMoveToRow){
		
		for(Queen qq:currentState.config){
			
			if(!qq.equal(q)){
				
				if(qq.location.y==q.location.y&&qq.location.x==nextMoveToRow){
					return true;
				}
			}
		}
		return false;
	}
	
}
