---
title: CRYPT_GEN_RANDOM (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CRYPT_GEN_RANDOM_TSQL
- CRYPT_GEN_RANDOM
dev_langs:
- TSQL
helpviewer_keywords:
- CRYPT_GEN_RANDOM function
ms.assetid: b74bd9d4-758e-4b94-89a0-76dcda6d8c42
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 695af04a3ee411392cf00be6b6483c9338a4c989
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="cryptgenrandom-transact-sql"></a>CRYPT_GEN_RANDOM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne un nombre aléatoire de chiffrement généré par l'API Crypto (CAPI). La sortie est un nombre hexadécimal du nombre d'octets spécifié.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
CRYPT_GEN_RANDOM ( length [ , seed ] )   
```  
  
## <a name="arguments"></a>Arguments  
*length*  
Longueur du nombre créé. La valeur maximale est 8 000. *length* est de type **int**.
  
*seed*  
Données facultatives à utiliser comme valeur de départ aléatoire.  Le nombre d’octets de données doit être supérieur ou égal à *length*. *seed* est de type **varbinary(8000)**.
  
## <a name="returned-types"></a>Types retournés  
**varbinary(8000)**
  
## <a name="permissions"></a>Autorisations  
Cette fonction est publique et ne requiert pas d'autorisation spéciale.
  
## <a name="examples"></a>Exemples  
  
### <a name="a-generating-a-random-number"></a>A. Génération d'un nombre aléatoire  
L'exemple suivant génère un nombre aléatoire d'une longueur de 50 octets.
  
```sql
SELECT CRYPT_GEN_RANDOM(50) ;  
```  
  
L'exemple suivant génère un nombre aléatoire d'une longueur de 4 octets à l'aide d'une valeur de départ de 4 octets.
  
```sql
SELECT CRYPT_GEN_RANDOM(4, 0x25F18060) ;  
```  
  
## <a name="see-also"></a>Voir aussi
[RAND &#40;Transact-SQL&#41;](../../t-sql/functions/rand-transact-sql.md)
  
  
