Combinations
============

    public void combinations(String input) {
      doCombine("", input);
    }
  
    public void doCombine(String prefix, String input) {
      System.out.println(prefix);
      for(int i = 0; i < input.length(); i++) {
        doCombine(prefix + input.charAt(i), input.substring(i+1));
      } 
    }