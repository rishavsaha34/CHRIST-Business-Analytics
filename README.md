# CHRIST-Business-Analytics

1. 
--Tree with maximum dimater
SELECT MAX(tree_dbh) as max_Diamater
FROM `bigquery-public-data.new_york.tree_census_2015` 

2.
--Number of Boroughs where trees are located 
SELECT count(distinct boroname)
FROM `bigquery-public-data.new_york.tree_census_2015` 

3.
--Tree ID's in ascending order with good health
SELECT tree_id , health
FROM `bigquery-public-data.new_york.tree_census_2015` 
Where health = 'Good'
order by tree_id  
limit 1000

4.
--Number of Trees per Zip Code
SELECT zipcode , count(tree_id) as Number_of_Trees
FROM `bigquery-public-data.new_york.tree_census_2015` 
group by zipcode

5.
--Number of Trees with their common names, having a count of more than 60000
SELECT spc_common , count(tree_id) as Number_of_Trees 
FROM `bigquery-public-data.new_york.tree_census_2015` 
group by spc_common 
Having count(tree_id) > 60000

6. 
--Number of Trees with Guards and their categories
SELECT guards , count(tree_id) as Number_of_Trees 
FROM `bigquery-public-data.new_york.tree_census_2015` 
group by guards 

7.
--Number of trees with Stmup Diameter more than 130
SELECT stump_diam , count(tree_id) as Number_of_Trees
FROM `bigquery-public-data.new_york.tree_census_2015` 
group by  stump_diam
HAVING stump_diam > 130
order by stump_diam desc 

8.
-- Number of Pin Oak with and without root stone
SELECT root_stone , spc_common, count(tree_id) as Number_of_Trees
FROM `bigquery-public-data.new_york.tree_census_2015` 
group by spc_common, root_stone
having spc_common = 'pin oak'

9.
SELECT latitude , health
FROM `bigquery-public-data.new_york.tree_census_2015` 
Where latitude >= 40.91200000
order by latitude  desc 

10.
-- Coordinates of tree with the thickest diameter
SELECT x_sp, y_sp , tree_dbh
FROM `bigquery-public-data.new_york.tree_census_2015` 
order by tree_dbh desc 
limit 10
