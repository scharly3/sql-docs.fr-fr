---
title: Création d’une Application de fournisseur SQL Server Native Client OLE DB | Documents Microsoft
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-ole-db-provider
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, application creation
- applications [SQL Server Native Client]
- OLE DB, creating applications
ms.assetid: f3ae6815-f32d-4913-a1a2-2ba2f20cfd88
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 192522a723e5a24cfea07e5a02b3ea4cb6663ae4
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="creating-a-sql-server-native-client-ole-db-provider-application"></a>Création d'une application de fournisseur OLE DB de SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Création d’un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] implique l’application du fournisseur OLE DB Native Client comme suit :  
  
1.  Établissement d'une connexion à une source de données.  
  
2.  Exécution d'une commande.  
  
3.  Traitement des résultats.  
  
> [!NOTE]  
>  Lorsque c'est possible, utilisez l'authentification Windows. Si l'authentification Windows n'est pas disponible, invitez les utilisateurs à entrer leurs informations d'identification au moment de l'exécution. Évitez de stocker ces informations dans un fichier. Si vous devez conserver les informations d’identification, chiffrez-les avec [cryptoAPI Win32](http://go.microsoft.com/fwlink/?LinkId=9504).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [L’établissement d’une connexion à une Source de données](../../relational-databases/native-client-ole-db-provider/establishing-a-connection-to-a-data-source.md)  
  
-   [Exécution d’une commande](../../relational-databases/native-client-ole-db-provider/executing-a-command.md)  
  
-   [Le traitement des résultats](../../relational-databases/native-client-ole-db-provider/processing-results.md)  
  
-   [À propos d’OLE DB, propriétés](../../relational-databases/native-client-ole-db-provider/about-ole-db-properties.md)  
  
-   [À l’aide de la Clause OUTPUT avec OLE DB dans SQL Server Native Client](../../relational-databases/native-client-ole-db-provider/using-the-output-clause-with-ole-db-in-sql-server-native-client.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
