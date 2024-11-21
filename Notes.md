### **Graph Theory & Adjacency Matrix**

1. **What is the degree of vertex 2 in the given undirected graph?**  
   A) 2  
   B) 3  
   C) 4 (Correct Answer)  
   D) 5  
   **Explanation:** The degree of a vertex is the number of edges connected to it. Count the edges starting or ending at vertex 2.

2. **How many edges are there in a complete graph with 6 vertices?**  
   A) 12  
   B) 15 (Correct Answer)  
   C) 20  
   D) 30  
   **Explanation:** A complete graph connects every pair of vertices. The formula for edges is \( n(n-1)/2 \), where \( n = 6 \).

3. **What does the diagonal element of an adjacency matrix represent?**  
   A) The number of edges  
   B) A self-loop (Correct Answer)  
   C) The weight of an edge  
   D) The total degree  
   **Explanation:** If a vertex has a self-loop, the diagonal element in its adjacency matrix is 1.

4. **Which graph has all vertices with the same degree?**  
   A) Regular Graph (Correct Answer)  
   B) Bipartite Graph  
   C) Directed Graph  
   D) Weighted Graph  
   **Explanation:** In a regular graph, all vertices have the same number of connections (degree).

5. **What is the minimum number of edges required for a connected graph with 8 vertices?**  
   A) 7 (Correct Answer)  
   B) 8  
   C) 9  
   D) 10  
   **Explanation:** A connected graph must have at least \( n-1 \) edges, where \( n \) is the number of vertices.

6. **How can you check if a graph is Eulerian?**  
   A) All vertices have odd degrees  
   B) All vertices have even degrees (Correct Answer)  
   C) The graph is bipartite  
   D) The graph has a cycle  
   **Explanation:** An Eulerian graph allows you to traverse every edge exactly once and return to the starting point; this happens if all vertices have even degrees.

7. **What type of graph can be represented by an adjacency matrix with all off-diagonal elements as 1?**  
   A) Null Graph  
   B) Path Graph  
   C) Complete Graph (Correct Answer)  
   D) Cyclic Graph  
   **Explanation:** A complete graph has all vertices connected to one another, represented by 1s in all off-diagonal elements.

8. **What is the sum of the degrees of all vertices in a graph with 10 edges?**  
   A) 10  
   B) 20 (Correct Answer)  
   C) 30  
   D) 40  
   **Explanation:** The sum of all vertex degrees equals twice the number of edges because each edge connects two vertices.

9. **What is a bipartite graph?**  
   A) A graph with no cycles  
   B) A graph with two sets of vertices where edges connect vertices from different sets (Correct Answer)  
   C) A complete graph  
   D) A graph with one vertex  
   **Explanation:** In a bipartite graph, vertices can be divided into two groups such that no two vertices in the same group are connected.

10. **Which of these is NOT true about an adjacency matrix?**  
    A) It is symmetric for undirected graphs  
    B) It represents self-loops with diagonal elements  
    C) It is always sparse (Correct Answer)  
    D) It can represent weighted graphs  
    **Explanation:** Adjacency matrices can be dense (many non-zero values) depending on the graph.

---

### **AWS and Cloud Metrics**

11. **Which AWS service is best for running serverless functions?**  
    A) EC2  
    B) Lambda (Correct Answer)  
    C) S3 Glacier  
    D) VPC  
    **Explanation:** AWS Lambda runs code without the need to manage servers, making it ideal for serverless applications.

12. **Which AWS storage option is used for archiving rarely accessed data?**  
    A) S3 Glacier (Correct Answer)  
    B) DynamoDB  
    C) EC2  
    D) RDS  
    **Explanation:** S3 Glacier is a low-cost storage service optimized for data that is rarely accessed.

13. **What does an AWS VPC do?**  
    A) Stores files  
    B) Provides isolated cloud networking (Correct Answer)  
    C) Hosts virtual machines  
    D) Runs serverless apps  
    **Explanation:** A Virtual Private Cloud (VPC) lets you create isolated networks within AWS.

14. **What is measured by the uptime percentage of a cloud service?**  
    A) Fault tolerance  
    B) System availability (Correct Answer)  
    C) Latency  
    D) Scalability  
    **Explanation:** Uptime percentage reflects how consistently a service is available without interruptions.

15. **What does MTBF measure in cloud systems?**  
    A) Latency  
    B) Mean Time Between Failures (Correct Answer)  
    C) Response Time  
    D) Uptime  
    **Explanation:** MTBF indicates the average time between system failures, reflecting reliability.

16. **Which AWS database is a NoSQL service?**  
    A) RDS  
    B) DynamoDB (Correct Answer)  
    C) S3  
    D) Aurora  
    **Explanation:** DynamoDB is Amazon's fully managed NoSQL database.

17. **Which AWS service distributes incoming traffic across multiple servers?**  
    A) CloudWatch  
    B) Load Balancer (Correct Answer)  
    C) Route 53  
    D) Lambda  
    **Explanation:** Load balancers distribute traffic to improve system performance and availability.

18. **What does Amazon S3 stand for?**  
    A) Simple Storage Service (Correct Answer)  
    B) Scalable Storage Solution  
    C) Serverless Storage System  
    D) Static Storage Service  
    **Explanation:** S3 is designed to store and retrieve any amount of data at any time.

19. **Which AWS service is commonly used for application monitoring?**  
    A) Lambda  
    B) CloudWatch (Correct Answer)  
    C) EC2  
    D) VPC  
    **Explanation:** Amazon CloudWatch collects and monitors logs and metrics for AWS services.

20. **What is scalability in cloud computing?**  
    A) Improving network speed  
    B) Increasing resources as needed (Correct Answer)  
    C) Reducing latency  
    D) Increasing system reliability  
    **Explanation:** Scalability refers to the ability of a system to handle increased demand by adding resources.

---

### **Database Management & Normalization**

21. **Which normalization removes repeating groups?**  
    A) 1NF (Correct Answer)  
    B) 2NF  
    C) 3NF  
    D) BCNF  
    **Explanation:** 1NF ensures data is in atomic form, removing repeating groups in a table.

22. **What is the purpose of BCNF in normalization?**  
    A) Remove multi-valued dependencies  
    B) Ensure every determinant is a key (Correct Answer)  
    C) Avoid transitive dependencies  
    D) Eliminate duplicate records  
    **Explanation:** BCNF ensures that all functional dependencies in a table use a candidate key as the determinant.

23. **Which SQL keyword removes duplicate rows?**  
    A) DISTINCT (Correct Answer)  
    B) UNIQUE  
    C) ALL  
    D) SELECT  
    **Explanation:** `DISTINCT` filters duplicate rows from the results.

24. **Which SQL command is used to update data in a table?**  
    A) INSERT  
    B) DELETE  
    C) UPDATE (Correct Answer)  
    D) ALTER  
    **Explanation:** The `UPDATE` statement modifies existing records in a database table.

25. **What is the primary purpose of an index in a database?**  
    A) To store more data  
    B) To speed up query execution (Correct Answer)  
    C) To ensure data integrity  
    D) To remove duplicates  
    **Explanation:** Indexes help databases locate data quickly without scanning the entire table.

26. **What is a foreign key in a database?**  
    A) A unique identifier for each record  
    B) A key referencing a primary key in another table (Correct Answer)  
    C) A key that enforces data uniqueness  
    D) A composite key  
    **Explanation:** A foreign key establishes relationships between two tables by referencing a primary key in another table.

27. **What does the SQL keyword `HAVING` do?**  
    A) Filters rows before grouping  
    B) Filters groups after aggregation (Correct Answer)  
    C) Sorts query results  
    D) Deletes rows from a table  
    **Explanation:** The `HAVING` clause filters data after aggregation, whereas `WHERE` filters rows before grouping.

28. **What is a composite primary key?**  
    A) A key made up of multiple columns (Correct Answer)  
    B) A foreign key in another table  
    C) A primary key with duplicates  
    D) A key that enforces referential integrity  
    **Explanation:** A composite key uses two or more columns together as a unique identifier for each record.

29. **Which of these is NOT a valid SQL aggregate function?**  
    A) COUNT  
    B) SUM  
    C) AVERAGE (Correct Answer)  
    D) MAX  
    **Explanation:** The correct function for calculating the average is `AVG`, not `AVERAGE`.

30. **Which normal form addresses transitive dependencies?**  
    A) 1NF  
    B) 2NF  
    C) 3NF (Correct Answer)  
    D) BCNF  
    **Explanation:** 3NF eliminates transitive dependencies by ensuring non-prime attributes depend only on candidate keys.

31. **What is the difference between `DELETE` and `TRUNCATE` in SQL?**  
    A) `DELETE` is faster  
    B) `TRUNCATE` removes all rows and cannot be rolled back (Correct Answer)  
    C) `TRUNCATE` deletes specific rows  
    D) `DELETE` cannot be filtered  
    **Explanation:** `DELETE` removes rows selectively and supports rollback; `TRUNCATE` clears all rows and is irreversible.

32. **What is a stored procedure in SQL?**  
    A) A precompiled set of SQL statements stored in the database (Correct Answer)  
    B) A method for creating tables  
    C) A backup function  
    D) A command for indexing data  
    **Explanation:** A stored procedure is a reusable piece of SQL code stored in the database to execute complex queries or logic.

---

### **Networking**

33. **Which layer of the OSI model is responsible for routing data between devices?**  
    A) Physical Layer  
    B) Data Link Layer  
    C) Network Layer (Correct Answer)  
    D) Application Layer  
    **Explanation:** The Network Layer (Layer 3) determines the best path to route packets to their destination.

34. **What is the function of a DNS server?**  
    A) It routes IP packets  
    B) It translates domain names to IP addresses (Correct Answer)  
    C) It assigns MAC addresses  
    D) It encrypts data packets  
    **Explanation:** DNS servers resolve human-readable domain names (like `example.com`) to machine-readable IP addresses.

35. **What is the purpose of the TCP three-way handshake?**  
    A) To authenticate devices  
    B) To establish a reliable connection between two devices (Correct Answer)  
    C) To encrypt data during transmission  
    D) To reset a connection  
    **Explanation:** The three-way handshake ensures a reliable connection by synchronizing and acknowledging packets.

36. **What is the default port number for HTTPS?**  
    A) 21  
    B) 80  
    C) 443 (Correct Answer)  
    D) 25  
    **Explanation:** HTTPS (HyperText Transfer Protocol Secure) uses port 443 by default for encrypted communication.

37. **Which protocol is used to transfer files between a client and a server?**  
    A) FTP (Correct Answer)  
    B) SMTP  
    C) HTTP  
    D) DHCP  
    **Explanation:** File Transfer Protocol (FTP) is designed for transferring files between computers over a network.

38. **What is the primary difference between IPv4 and IPv6?**  
    A) IPv4 is faster than IPv6  
    B) IPv4 has a smaller address space than IPv6 (Correct Answer)  
    C) IPv6 is used only for internal networks  
    D) IPv4 supports encryption by default  
    **Explanation:** IPv6 provides a significantly larger address space compared to IPv4, allowing for more devices to connect to the internet.

39. **Which of these is a private IP address?**  
    A) 8.8.8.8  
    B) 192.168.1.1 (Correct Answer)  
    C) 172.217.0.0  
    D) 203.0.113.0  
    **Explanation:** Private IP addresses, like 192.168.x.x, are used for internal networks and cannot be routed on the internet.

40. **What does the term "ping" measure?**  
    A) Download speed  
    B) Round-trip time of a packet (Correct Answer)  
    C) Bandwidth  
    D) Packet loss  
    **Explanation:** `Ping` measures the time it takes for a packet to travel from a device to a server and back.

41. **What is the purpose of the DHCP protocol?**  
    A) Encrypt data packets  
    B) Assign IP addresses dynamically (Correct Answer)  
    C) Resolve domain names  
    D) Monitor network traffic  
    **Explanation:** DHCP (Dynamic Host Configuration Protocol) assigns IP addresses to devices automatically.

42. **What is the function of a subnet mask?**  
    A) To divide a network into smaller networks (Correct Answer)  
    B) To encrypt network traffic  
    C) To determine MAC addresses  
    D) To identify network protocols  
    **Explanation:** A subnet mask helps segment a larger network into smaller subnetworks to improve management and efficiency.

---

### **Programming & Logic**

43. **What is a recursive function?**  
    A) A function that runs in parallel  
    B) A function that calls itself (Correct Answer)  
    C) A function that compiles twice  
    D) A function with multiple loops  
    **Explanation:** A recursive function solves problems by calling itself with a smaller input.

44. **What is the time complexity of a binary search algorithm?**  
    A) \( O(n) \)  
    B) \( O(\log n) \) (Correct Answer)  
    C) \( O(n^2) \)  
    D) \( O(1) \)  
    **Explanation:** Binary search divides the search space in half, reducing the search time to logarithmic complexity.

45. **Which sorting algorithm is the fastest on average?**  
    A) Bubble Sort  
    B) Insertion Sort  
    C) Merge Sort (Correct Answer)  
    D) Selection Sort  
    **Explanation:** Merge Sort has an average and worst-case time complexity of \( O(n \log n) \), making it faster than simpler algorithms.

46. **What is a stack data structure?**  
    A) A collection with First-In-First-Out (FIFO) order  
    B) A collection with Last-In-First-Out (LIFO) order (Correct Answer)  
    C) A priority-based collection  
    D) An unsorted list  
    **Explanation:** A stack adds and removes elements in a LIFO order, like a stack of plates.

47. **What is the base case in recursion?**  
    A) The smallest input that stops recursion (Correct Answer)  
    B) A loop in the function  
    C) The maximum recursion depth  
    D) The return value  
    **Explanation:** The base case prevents infinite recursion by defining when the recursive function should stop.

48. **What is an infinite loop?**  
    A) A loop that runs until the condition is false  
    B) A loop that never terminates (Correct Answer)  
    C) A loop with a fixed number of iterations  
    D) A loop with no condition  
    **Explanation:** Infinite loops occur when the condition for termination is never met.

49. **What is the difference between an array and a linked list?**  
    A) Arrays are faster for insertions  
    B) Linked lists are fixed in size  
    C) Arrays have fixed size, whereas linked lists grow dynamically (Correct Answer)  
    D) Linked lists use contiguous memory  
    **Explanation:** Arrays have a predefined size, while linked lists dynamically allocate memory.

50. **What is the purpose of exception handling in programming?**  
    A) To prevent bugs  
    B) To handle errors gracefully during runtime (Correct Answer)  
    C) To optimize code  
    D) To terminate the program  
    **Explanation:**

 Exception handling allows programs to continue running or take specific actions when an error occurs.
