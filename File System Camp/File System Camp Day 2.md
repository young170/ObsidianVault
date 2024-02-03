
Everything is in the Super Block
* ![[Pasted image 20240119110817.png]]
* ![[Screenshot 2024-01-19 at 10.59.42 1.png]]
* From the Boot Record to the first FAT area is called the **Reserved Sector** or Rsvd S.
	* Using Bytes Per Sector * Rsvd S. Count can get the address of the first FAT
		* 0x215C00
		* ![[Screenshot 2024-01-19 at 10.59.55.png]]
* After the 2 FAT areas is the data area
	* (num of sectors of FAT * bytes per sector * 2) + offset
		* 0x400000
		* ![[Screenshot 2024-01-19 at 11.00.06.png]]
* ![[Pasted image 20240119112244.png]]
	* Attributes
* ![[Pasted image 20240119112312.png]]
	* deleted file has 0xE5 in the first bit of the file name
* ![[Pasted image 20240119112713.png]]
	* follow 0x00000006
* ![[Pasted image 20240119112650.png]]
	* find files

### Recovering LEAF.jpg
1. Get the cluster numbers of the file LEAF.jpg
	1. ![[Pasted image 20240119114631.png]]
2. Get the file size to know how much we need to extract
	1. ![[Pasted image 20240119114707.png]]
	2. which is 0x0008F06F due to little endian
3. Copy from 0x405000 to 0x49406F
	1. 0x405000 + 0x0008F06F = 0x49406F
	2. ![[LEAF.png]]
	3. BAM

### Recovering TIGER.jpg
It is a deleted file so its cluster is cleared to FF FF FF 0F
Have to use file size to extract data

