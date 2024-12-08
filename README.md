package ooplabb;
import java.util.ArrayList;
import java.util.Scanner;
class Candidate {
 private String name;
 private int voteCount;
 public Candidate(String name) {
 this.name = name;
 this.voteCount = 0;
 }
 public void incrementVote() {
 voteCount++;
 }
public int getVoteCount() {
 return voteCount;
 }
 public String getName() {
 return name;
 }
}
public class votingSystem {
 private ArrayList<Candidate> candidates;
 private int numVoters;
 public votingSystem() {
 candidates = new ArrayList<>();
 }
 public void addCandidate(String name) {
 candidates.add(new Candidate(name));
 }
 public void setNumVoters(int numVoters) {
 this.numVoters = numVoters;
 }
 public void vote() {
 Scanner scanner = new Scanner(System.in);
 for (int i = 0; i < numVoters; i++) {
 System.out.println("\nVote #" + (i + 1));
 for (int j = 0; j < candidates.size(); j++) {
 System.out.println((j + 1) + ". " + candidates.get(j).getName());
 }
 System.out.print("Select your candidate (1 to " + candidates.size() + "): ");
 int choice = scanner.nextInt()
 if (choice >= 1 && choice <= candidates.size()) {
 candidates.get(choice - 1).incrementVote();
 System.out.println("Vote recorded for " + candidates.get(choice - 1).getName());
 } else {
 System.out.println("Invalid choice. Try again.");
 i--;
 }
 }
 }
 public void displayResults() {
 System.out.println("\nVoting Results:");
 Candidate winner = candidates.get(0);
 for (Candidate candidate : candidates) {
 System.out.println(candidate.getName() + ": " + candidate.getVoteCount() + " votes");
 if (candidate.getVoteCount() > winner.getVoteCount()) {
 winner = candidate;
 }
 }
 System.out.println("\nThe winner is: " + winner.getName());
 }
 public static void main(String[] args) {
 Scanner scanner = new Scanner(System.in);
 votingSystem system = new votingSystem();
 System.out.print("Enter the number of candidates: ");
 int numCandidates = scanner.nextInt();
 scanner.nextLine();
 for (int i = 0; i < numCandidates; i++) {
 System.out.print("Enter name for Candidate " + (i + 1) + ": ");
 String candidateName = scanner.nextLine();
 system.addCandidate(candidateName);
 }
 System.out.print("Enter the number of voters: ");
 int numVoters = scanner.nextInt();
 system.setNumVoters(numVoters);
 system.vote();
 system.displayResults();
