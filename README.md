# Programming-210-Assignment-1

#include <stdio.h>
#include <math.h>
#include <string.h>
#include <stdlib.h>


int main(void)
{
	char first_string_vector[20], second_string_vector[20];
	double first_vector[20], second_vector[20], merged_vector[20];
	double temp = 0, value = 0;
	char *sPtr;
	int a = 0, b = 0, i = 0, j = 0, k = 0;

	for (i=0; i <= 19; i++)											//set all array locations to 0
	{
		first_vector[i] = 0;
		second_vector[i] = 0;
		first_string_vector[i] = 0;
		second_string_vector[i] = 0;
		merged_vector[i] = 0;
	}

	printf("Enter the elements of the first vector: ");				//read the 1st string
	gets(first_string_vector);
	printf("Enter the elements of the second vector: ");			//read the 2nd string
	gets(second_string_vector);

	a = 0;
	sPtr = strtok(first_string_vector, " ");						 //converts the first string to double
	while(sPtr != NULL)
	{
		value = strtod(sPtr, NULL);
		first_vector[a] = value;
		a++;
		sPtr = strtok(NULL, " ");
	} 

	a = 0;
	sPtr = strtok(second_string_vector, " ");						 //converts the second string to double
	while (sPtr != NULL)
	{
		value = strtod(sPtr, NULL);
		second_vector[a] = value;
		a++;
		sPtr = strtok(NULL, " ");
	}

	for (a = 0; a <= 10; a++)										 //sorts the first vector into ascending order
	{
		for (b=a+1; b<=10; b++)
		{
			if (first_vector[a] > first_vector[b] && first_vector[b] != 0)
			{
				temp = first_vector[a];
				first_vector[a] = first_vector[b];
				first_vector[b] = temp;
			}
		}
	}

	for (a = 0; a <= 10; a++)										 //sorts the second vector into ascending order
	{
		for (b = a + 1; b <= 10; b++)
		{
			if (second_vector[a] > second_vector[b] && second_vector[b] != 0)
			{
				temp = second_vector[a];
				second_vector[a] = second_vector[b];
				second_vector[b] = temp;
			}
		}
	}

	k = 0; a = 0; b = 0;											//
	while (k < 35 && first_vector[a]!=0 && second_vector[b]!=0)		//Merges the 2 vectors into a 
																	//single array in ascending order
	{																//
		if (first_vector[a] < second_vector[b])
		{
			merged_vector[k] = first_vector[a];
			a++;
		}
		else
		{
			merged_vector[k] = second_vector[b];
			b++;
		}
		k++;
	}

	if (first_vector[a] != 0)										//Checks to see if there
	{																//are any left over vectors
		while (first_vector[a] != 0)								//in the first array
		{															//after merging
			merged_vector[k] = first_vector[a];
			a++; k++;
		}
	}
	else if(second_vector[b] != 0)									//Checks to see if there
	{																//are any left over vectors
		while (second_vector[b] != 0)								//in the second array
		{															//after merging
			merged_vector[k] = second_vector[b];
			b++; k++;
		}
	}

	a = 0;
	printf("\nThe sorted first vector:");							//Prints the first array in
	while (first_vector[a] != 0)									//ascending order
	{																 
		printf(" %.1f", first_vector[a]);							
		a++;
	}

	a = 0;
	printf("\nThe sorted second vector:");							//Prints the second array in
	while (second_vector[a] != 0)									//ascending order
	{
		printf(" %.1f", second_vector[a]);
		a++;
	}

	a = 0;
	printf("\nThe result of merging the first and second vectors:");//Prints the first array in
	while (merged_vector[a] != 0)									//ascending order
	{
		printf(" %.1f", merged_vector[a]);
		a++;
	}

	getch();
}
