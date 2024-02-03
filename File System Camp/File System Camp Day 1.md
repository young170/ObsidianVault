
file system forensic starts from the root

https://stackoverflow.com/questions/20209754/in-linux-how-many-superblocks-are-there-per-file-system
* multiple superblocks
* what if the main superblock is corrupted, but doesn't cause explicit errors such as loops?
	* compare with other superblocks?

keeping a consistent pattern/rule of the system makes converting between other system rules of efficient

When considering cases where the (input) data is corrupted, in the forensic's perspective, using **prior** knowledge, using start-end + patterns recovering is possible

![[Pasted image 20240118144111.png]]
#### Super Block
the information desk of the building (file system)
* size, location, root (starting point, elevator of the building)

#### Bitmap
focuses on **availability**
* a minimap
in forensic's POV: focuses on the unused bits (unallocated memory) the "deleted" but not removed. Uses **carving** to extract the data
* What is carving? just like archaeologists, finding structures in unstructured data
* by changing the definition of "unallocated" to "failed to recover", which counts deleted data too, carving is more effective

### Forensic Steps
1. check super block for f/s geometry
2. traverse all dirs for all inodes
3. if the f/s has a journal, then check journal for additional data
4. record unallocated data

### FAT (File Allocation Table)
File "allocation" table
* general bitmap
inode table is integrated to the data table
File size block is 4 bytes, 32bits, 2^32 is 4GB

### exFAT
chaining + ext method
for continuous memory, such as videos, insertion is frequently needed so chaining is used

### Terms
* Filesystem: structure + rules
* Slack: because CPU considers I/O time over memory computational time, unused space between storages are called slacks
	* very focused on speed, memory space is cheap
	* example: a new entry in a dairy
	* how is this useful in forensic? how pen ink fades into the next page, some data is left
	* slack space :- The “Slack Space” in a nutshell, is the unused space between the end of a stored file, and the end of a given data unit, also known as cluster or block. When a file is written into the disk, and it doesn’t occupy the entire cluster, the remaining space is called slack space. Slack space is the leftover storage that exists on a computer’s hard disk drive when a computer file does not need all the space it has been allocated by the operating system. The examination of slack space is an important aspect of computer forensics. Slack space is an important form of evidence in the field of forensic investigation. Often, slack space can contain relevant information about a suspect that a prosecutor can use in a trial. (https://medium.com/@abhinavnandgaonkar98/anti-forensic-techniques-secure-deletion-file-hiding-e61137d00d9f)
	* Primarily three different types of slack space
		* RAM Slack: Unused space between the end of the logical file and the end of the memory page.
		* File Slack: Unused sectors within the last sector the file occupies
		* Volume/partition slack: Unused space between the end of the filesystem and the end of the partition that it occupies
* trim
	* same as zero-izing
* cluster-chain
	* implemented using SLL, the inodes of FAT are connected
	* contrastly, EXT uses block-pointer to connect the inodes
		* overhead due to the pointers
		* EXT-4 pointers just record start & end
			* disregards the file size, just where it is located/separated
* inode: index-node

### External
why do we use tree structures? fast search
* overhead of the balancing action
* inserting in bulks (for B+ trees) are more efficient
producer-consumer
* bounded-queue
Good coding
* check all return of APIs
Keep compatibility/change in mind
* ex. FAT 12/16/32
* the 2nd cluster wasn't used for 12/16, later when 32-bit addr was used
lazy vs eager
sparse
COW (Copy On Write)
* copy constructor of C++
Log의 어원
* tree log
* sailers logged on logs because logs survive after wrecks
Using streams (fstream) is for continuous flow of data
* continuous "view" of data, using abstraction