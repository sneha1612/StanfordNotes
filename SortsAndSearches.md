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

Quick Sort
=========

    public void quickSort(int[] arr) {
      sort(arr, 0, arr.length-1);
    }

    public void sort(int[] arr, int low, int high) {
      if(low < high) {
        int index = partition(arr, low, high);
        sort(arr, low, index-1);
        sort(arr, index+1, high);
      }
    }

    public int partition(int[] arr, int low, int high) {
      int pivot = arr[high];
      int i = low-1;
      for(int j = low; j<high; j++) {
        if(arr[j] <= pivot) {
          i = i+1;
          
          int temp = arr[i];
          arr[i] = arr[j];
          arr[j] = temp;
        }
      }
        
      int t = arr[i+1];
      arr[i+1] = arr[high];
      arr[high] = t;

      return i+1;
    }

Merge Sort
==========

    public void mergeSort(int[] arr) {
      sort(arr, 0, arr.length-1);
    }

    public void sort(int[] arr, int p, int r) {
      int q = (p+r)/2;
      sort(arr, p, q);
      sort(arr, q+1, r);
      merge(arr, p, q, r);
    }

    public void merge(int[] arr, int p, int q, int r) {
      int n1 = p+q-1;
      int n2 = r-q;

      int[] left = new int[n1+1];
      int[] right = new int[n2+1];

      left[n1] = Integer.MAX_VALUE;
      left[n2] = Integer.MAX_VALUE;

      for(int i = 0; i<n1; i++) {
        left[i] = arr[p+i];
      }

      for(int j=0; j<n2; j++) {
        right[j] = arr[q+j+1];
      }

      int x = 0;
      int y = 0;

      for(int k = p; k <=r; k++) {
        if(left[x] <= right[y]) {
          arr[k] = left[x];
          x++;
        } else {
          arr[k] = right[y];
          y++;
        }
      }
    }

Bubble Sort
===========

    public void bubbleSort(int[] arr) {
      for(int i = 0; i < arr.length -1; i++) {
        for(int j = 0; j < arr.length - i-1; j++) {
          if(arr[j] > arr[j+1]) {
            int temp = arr[j];
            arr[j] = arr[j+1];
            arr[j+1] = temp;
          }
        }
      }
    }

Selection Sort
==============

    public void selectionSort(int[] arr) {
      for(int i = 0; i<arr.length-1; i++) {
        for(int j = i+1; j<arr.length; j++) {
          if(arr[i] > arr[j]) {
            int temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;
          }
        }
      }
    }

Insertion Sort
==============

    public void insertionSort(int[] arr) {
      for(int i = 1; i < arr.length; i++) {
        int temp = arr[i];
        int j = i;
        while(j > 0 && temp < arr[j-1]) {
          arr[j] = arr[j-1];
          j--;
        }
        arr[j] = temp;
      }
    }

