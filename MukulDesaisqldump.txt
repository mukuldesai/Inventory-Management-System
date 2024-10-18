-- MySQL dump 10.13  Distrib 8.1.0, for Win64 (x86_64)
--
-- Host: localhost    Database: ims
-- ------------------------------------------------------
-- Server version	8.1.0

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!50503 SET NAMES utf8mb4 */;
/*!40103 SET @OLD_TIME_ZONE=@@TIME_ZONE */;
/*!40103 SET TIME_ZONE='+00:00' */;
/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;

--
-- Table structure for table `brands`
--

DROP TABLE IF EXISTS `brands`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `brands` (
  `bid` int NOT NULL,
  `bname` varchar(20) DEFAULT NULL,
  PRIMARY KEY (`bid`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `brands`
--

LOCK TABLES `brands` WRITE;
/*!40000 ALTER TABLE `brands` DISABLE KEYS */;
INSERT INTO `brands` VALUES (1,'Apple'),(2,'Samsung'),(3,'Nike'),(4,'Fortune');
/*!40000 ALTER TABLE `brands` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `categories`
--

DROP TABLE IF EXISTS `categories`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `categories` (
  `cid` int NOT NULL,
  `category_name` varchar(20) DEFAULT NULL,
  PRIMARY KEY (`cid`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `categories`
--

LOCK TABLES `categories` WRITE;
/*!40000 ALTER TABLE `categories` DISABLE KEYS */;
INSERT INTO `categories` VALUES (1,'Electronics'),(2,'Clothing'),(3,'Grocey');
/*!40000 ALTER TABLE `categories` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `customer_cart`
--

DROP TABLE IF EXISTS `customer_cart`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `customer_cart` (
  `cust_id` int NOT NULL,
  `name` varchar(20) DEFAULT NULL,
  `mobno` int DEFAULT NULL,
  PRIMARY KEY (`cust_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `customer_cart`
--

LOCK TABLES `customer_cart` WRITE;
/*!40000 ALTER TABLE `customer_cart` DISABLE KEYS */;
INSERT INTO `customer_cart` VALUES (1,'Ram',987654321),(2,'Shyam',987654320),(3,'Mohan',987654323);
/*!40000 ALTER TABLE `customer_cart` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `inv_user`
--

DROP TABLE IF EXISTS `inv_user`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `inv_user` (
  `user_id` varchar(20) NOT NULL,
  `name` varchar(20) DEFAULT NULL,
  `password` varchar(20) DEFAULT NULL,
  `last_login` timestamp NULL DEFAULT NULL,
  `user_type` varchar(10) DEFAULT NULL,
  PRIMARY KEY (`user_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `inv_user`
--

LOCK TABLES `inv_user` WRITE;
/*!40000 ALTER TABLE `inv_user` DISABLE KEYS */;
INSERT INTO `inv_user` VALUES ('kunal@gmail.com','Kunal Khandelwal','1111','2023-10-04 14:20:00','Manager'),('mukul@gmail.com','mukul','123','2023-12-01 06:43:00','admin'),('prashant@gmail.com','Prashant Sharma','0011','2023-10-29 14:20:00','Accountant');
/*!40000 ALTER TABLE `inv_user` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `invoice`
--

DROP TABLE IF EXISTS `invoice`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `invoice` (
  `item_no` int DEFAULT NULL,
  `product_name` varchar(20) DEFAULT NULL,
  `quantity` int DEFAULT NULL,
  `net_price` int DEFAULT NULL,
  `transaction_id` int DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `invoice`
--

LOCK TABLES `invoice` WRITE;
/*!40000 ALTER TABLE `invoice` DISABLE KEYS */;
/*!40000 ALTER TABLE `invoice` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `product`
--

DROP TABLE IF EXISTS `product`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `product` (
  `pid` int NOT NULL,
  `cid` int DEFAULT NULL,
  `bid` int DEFAULT NULL,
  `sid` int DEFAULT NULL,
  `pname` varchar(20) DEFAULT NULL,
  `p_stock` int DEFAULT NULL,
  `price` int DEFAULT NULL,
  `added_date` date DEFAULT NULL,
  PRIMARY KEY (`pid`),
  KEY `sid` (`sid`),
  CONSTRAINT `product_ibfk_1` FOREIGN KEY (`sid`) REFERENCES `stores` (`sid`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `product`
--

LOCK TABLES `product` WRITE;
/*!40000 ALTER TABLE `product` DISABLE KEYS */;
INSERT INTO `product` VALUES (1,1,1,1,'IPHONE',7,80000,'2022-10-13'),(2,1,1,1,'Airpods',3,30000,'2022-10-29'),(3,1,1,1,'Smartwatch',3,20000,'2022-12-29'),(4,2,2,2,'Airmax',6,10000,'2022-08-12'),(5,3,4,3,'Oil',8,750,'2022-07-29');
/*!40000 ALTER TABLE `product` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `provides`
--

DROP TABLE IF EXISTS `provides`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `provides` (
  `bid` int DEFAULT NULL,
  `sid` int DEFAULT NULL,
  `discount` int DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `provides`
--

LOCK TABLES `provides` WRITE;
/*!40000 ALTER TABLE `provides` DISABLE KEYS */;
INSERT INTO `provides` VALUES (1,1,12),(2,2,7),(3,3,15),(1,2,7),(4,2,19),(4,3,20);
/*!40000 ALTER TABLE `provides` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `select_product`
--

DROP TABLE IF EXISTS `select_product`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `select_product` (
  `cust_id` int DEFAULT NULL,
  `pid` int DEFAULT NULL,
  `quantity` int DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `select_product`
--

LOCK TABLES `select_product` WRITE;
/*!40000 ALTER TABLE `select_product` DISABLE KEYS */;
INSERT INTO `select_product` VALUES (1,2,2),(1,3,1),(2,3,3),(3,2,1);
/*!40000 ALTER TABLE `select_product` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `stores`
--

DROP TABLE IF EXISTS `stores`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `stores` (
  `sid` int NOT NULL,
  `sname` varchar(20) DEFAULT NULL,
  `address` varchar(20) DEFAULT NULL,
  `mobno` int DEFAULT NULL,
  PRIMARY KEY (`sid`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `stores`
--

LOCK TABLES `stores` WRITE;
/*!40000 ALTER TABLE `stores` DISABLE KEYS */;
INSERT INTO `stores` VALUES (1,'ketan','raket',111111111),(2,'ishan','potan',989898989),(3,'warne','lahor',898989898);
/*!40000 ALTER TABLE `stores` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `transaction`
--

DROP TABLE IF EXISTS `transaction`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `transaction` (
  `id` int NOT NULL,
  `total_amount` int DEFAULT NULL,
  `paid` int DEFAULT NULL,
  `due` int DEFAULT NULL,
  `gst` int DEFAULT NULL,
  `discount` int DEFAULT NULL,
  `payment_method` varchar(10) DEFAULT NULL,
  `cart_id` int DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `transaction`
--

LOCK TABLES `transaction` WRITE;
/*!40000 ALTER TABLE `transaction` DISABLE KEYS */;
INSERT INTO `transaction` VALUES (1,25000,20000,5000,350,350,'card',1),(2,57000,57000,0,570,570,'cash',2),(3,19000,17000,2000,190,190,'card',3);
/*!40000 ALTER TABLE `transaction` ENABLE KEYS */;
UNLOCK TABLES;
/*!40103 SET TIME_ZONE=@OLD_TIME_ZONE */;

/*!40101 SET SQL_MODE=@OLD_SQL_MODE */;
/*!40014 SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS */;
/*!40014 SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS */;
/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;
/*!40111 SET SQL_NOTES=@OLD_SQL_NOTES */;

-- Dump completed on 2023-12-15 14:50:17
