Linear Search
=============

    public int linearSearch(int[] arr, int val) {
      for(int i = 0; i<arr.length; i++) {
        if(val == arr[i])
          return i;
      }
      return -1;
    }

Binary Search
=============

    public int binarySearch(int[] arr, int val) {
      int low = 0;
      int high = arr.length -1;

      while(low < high) {
        mid = (low+high)/2;

        if(arr[mid] == val)
          return mid;
        else if(val < arr[mid])
          high = mid;
        else 
          low = mid+1;
      }
      return -1;
    }

    