# -Postgresql-

------------------- 生成自定义条数据 id 自增-----------------------------------------    
select *,'1' as col_2 ,'abc' as col_3 from generate_series(1,100) as id  
输出：  
![image](https://user-images.githubusercontent.com/51266324/195486261-975b5f21-92b7-43fa-b7d4-86fbbb7a3a3a.png)


------------------- 随机抽取自定义集合中的元素 --------------------------------------   
设定自定义集合array['A','B','C']作为参数，random_choice函数会随机抽取集合中的数据  
select random_choice(array['通过', '不通过']) from generate_series(1,100)
输出：  
![image](https://user-images.githubusercontent.com/51266324/195485944-eb3ba73a-f75d-4f95-bf61-cf27a7994e88.png)

-------------------- 随机生成基于md5哈希的名字---------------------------------------  
select md5(random()::text)   --用于id之类的生成
输出：  
![image](https://user-images.githubusercontent.com/51266324/195485900-729ae6e2-e2d0-4867-b1a0-3bdf5d1c86e7.png)

-------------------- 生成随机坐标 ---------------------------------------------------  
select round((random()::numeric*360-180),6) as lng,round((random()::numeric*170-85),6)
输出:  
![image](https://user-images.githubusercontent.com/51266324/195485801-877c3d0f-a803-4043-bc67-ab01b0788989.png)


------ 随机取a,b之间的整数 ----------------------------------------------------------  
select my_random_num(1,3)

-------------------- 生成随机姓名 ---------------------------------------------------  
创建 get_random_name()函数的之前要先创建自定义my_random_num()函数  
select get_random_name(-1) from generate_series(1,100) --输入1:生成男性姓名，输入2:生成女性姓名,输入-1,随机生成姓名
输出：   
![image](https://user-images.githubusercontent.com/51266324/195485162-1fe4b624-5a40-4c7e-ac4c-7d64b6e43120.png)

