#Implement Trie (Prefix Tree)#

##Problem##

Implement a trie with `insert`, `search`, and `startsWith` methods.

**Note:**
You may assume that all inputs are consist of lowercase letters `a-z`.

Subscribe to see which companies asked this question

##Code##

	class TrieNode {
	    // Initialize your data structure here.
	    public Boolean isEnd;
	    public HashMap<Character, TrieNode> children;
	    public TrieNode() {
	        children = new HashMap<Character, TrieNode>();
	        isEnd = false;
	    }
	}
	
	public class Trie {
	    private TrieNode root;
	
	    public Trie() {
	        root = new TrieNode();
	    }
	
	    // Inserts a word into the trie.
	    public void insert(String word) {
	        TrieNode now = root;
	        if (word == null || word.length() == 0) {
	            return;
	        }
	        for (int i = 0; i < word.length(); i++) {
	            Character c = word.charAt(i);
	            if (!now.children.containsKey(c)) {
	                now.children.put(c, new TrieNode());
	            }
	            now = now.children.get(c);
	        }
	        now.isEnd = true;
	    }
	
	    // Returns if the word is in the trie.
	    public boolean search(String word) {
	        TrieNode now = root;
	        if (word == null || word.length() == 0) {
	            return false;
	        }
	        for (int i = 0; i < word.length(); i++) {
	            Character c = word.charAt(i);
	            if (!now.children.containsKey(c)) {
	                return false;
	            }
	            now = now.children.get(c);
	        }
	        return now.isEnd;
	    }
	
	    // Returns if there is any word in the trie
	    // that starts with the given prefix.
	    public boolean startsWith(String prefix) {
	        TrieNode now = root;
	        for (int i = 0; i < prefix.length(); i++) {
	            Character c = prefix.charAt(i);
	            if (!now.children.containsKey(c)) {
	                return false;
	            }
	            now = now.children.get(c);
	        }
	        return true;
	    }
	
	}
	
##Solution and Analysis##


