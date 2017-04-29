---
title: "Utilisation d’OPENJSON avec un sch&#233;ma explicite (SQL&#160;Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "OPENJSON, avec schéma explicite"
ms.assetid: 9c1c3bfb-e1ad-4659-b94f-722b0848d5a2
caps.latest.revision: 13
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 12
---
# Utilisation d’OPENJSON avec un sch&#233;ma explicite (SQL&#160;Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Utilisez **OPENJSON** avec un schéma explicite pour renvoyer une table mise en forme telle que vous l’avez spécifiée dans la clause WITH.  
  
 Voici quelques exemples d’utilisation de **OPENJSON** avec un schéma explicite. Pour en savoir plus et obtenir d’autres exemples, consultez [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md).  
  
## Exemple : mettre en forme la sortie à l’aide de la clause WITH  
 La requête suivante renvoie les résultats présentés dans le tableau suivant. Notez qu’avec la clause AS JSON, les valeurs sont renvoyées dans col5 et array_element en tant qu’objets JSON au lieu de valeurs scalaires.  
  
```tsql  
DECLARE @json NVARCHAR(MAX) =
N'{"someObject":   
   {"someArray":  
     [  
         {"k1": 11, "k2": null, "k3": "text"},  
         {"k1": 21, "k2": "text2", "k4": { "data": "text4" }},  
         {"k1": 31, "k2": 32},  
         {"k1": 41, "k2": null, "k4": { "data": false }}     
      ]  
   }  
}'  
  
SELECT * FROM  
OPENJSON(@json, N'lax $.someObject.someArray')  
WITH ( k1 int,   
       k2 varchar(100),  
       col3 varchar(6) N'$.k3',  
       col4 varchar(10) N'lax $.k4.data',  
       col5 nvarchar(MAX) N'lax $.k4' AS JSON, 
       array_element nvarchar(MAX) N'$' AS JSON  
)  
```  
  
 **Résultats**  
  
|k1|k2|col3|col4|col5|array_element|  
|--------|--------|----------|----------|----------|--------------------|  
|11|*NULL*|"text"|*NULL*|*NULL*|{"k1": 11, "k2": null, "k3": "text"}|  
|21|"text2"|*NULL*|"text4"|{ "data": "text4" }|{"k1": true, "k2": "text2", "k4": { "data": "text4" } }|  
|31|"32"|*NULL*|*NULL*|*NULL*|{"k1": 31, "k2": 32 }|  
|41|*NULL*|*NULL*|false|{ "data": false }|{"k1": 41, "k2": null,       "k4": { "data": false }    }|  
  
## Exemple - chargement de JSON dans une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
 L’exemple suivant charge l’intégralité d’un objet JSON dans une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
```tsql  
declare @json nvarchar(max) = '{  
 "id" : 2,  
 "firstName": "John",  
 "lastName": "Smith",  
 "isAlive": true,  
 "age": 25,  
 "dateOfBirth": "2015-03-25T12:00:00",  
 "spouse": null  
 }';  
  
 INSERT INTO Person  
 SELECT *   
 FROM OPENJSON(@json)  
 WITH (id int,  
       firstName nvarchar(50), lastName nvarchar(50),   
       isAlive bit, age int,  
       dateOfBirth datetime2, spouse nvarchar(50))  
  
```  
  
## Voir aussi  
 [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md)  
  
  