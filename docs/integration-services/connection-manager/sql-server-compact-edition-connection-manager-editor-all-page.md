---
title: "&#201;diteur du gestionnaire de connexions SQL Server Compact Edition (page Tout) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.sqlmobileconnection.all.f1"
helpviewer_keywords: 
  - "Éditeur du gestionnaire de connexions SQL Server Compact"
ms.assetid: f9fbff4b-c502-44b3-8e7b-398d66e82206
caps.latest.revision: 26
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 26
---
# &#201;diteur du gestionnaire de connexions SQL Server Compact Edition (page Tout)
  La boîte de dialogue **Éditeur du gestionnaire de connexions SQL Server Compact Edition** permet de spécifier les propriétés permettant de se connecter à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 Pour en savoir plus sur le gestionnaire de connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact Edition, consultez [Éditeur du gestionnaire de connexions SQL Server Compact Edition](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager.md).  
  
## Options  
 **AutoShrink Threshold**  
 Spécifiez le pourcentage d’espace libre autorisé dans la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact avant que le processus de réduction automatique soit lancé.  
  
 **Escalade de verrous par défaut**  
 Spécifiez le nombre de verrous de base de données acquis par la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact avant qu’elle tente de promouvoir les verrous.  
  
 **Default Lock Timeout**  
 Spécifiez l'intervalle par défaut, en millisecondes, d'attente d'un verrou par une instruction.  
  
 **Flush Interval**  
 Spécifiez l'intervalle, en secondes, s'écoulant entre les vidages de données de transactions validées sur le disque.  
  
 **Identificateur de paramètres régionaux**  
 Spécifiez l’identificateur de paramètres régionaux (LCID) de la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 **Max Buffer Size**  
 Spécifiez la quantité maximale de mémoire (en Ko) utilisée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact avant d’effectuer un vidage des données sur le disque.  
  
 **Max Database Size**  
 Spécifiez la taille maximale (en Mo) de la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 **Mode**  
 Spécifiez le mode de fichier dans lequel ouvrir la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact. La valeur par défaut de cette propriété est **Read Write**.  
  
 L'option Mode comporte quatre valeurs, qui sont décrites dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|**Lecture seule**|Offre un accès en lecture seule à la base de données.|  
|**Read Write**|Autorise l'accès en lecture et écriture à la base de données.|  
|**Exclusive**|Offre un accès exclusif à la base de données.|  
|**Shared Read**|Indique que plusieurs utilisateurs peuvent lire la base de données simultanément.|  
  
 **Persist Security Info**  
 Indique si des informations de sécurité sont retournées dans la chaîne de connexion. La valeur par défaut de cette option est **False**.  
  
 **Temp File Directory**  
 Spécifiez l’emplacement du fichier de base de données temporaire de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 **Source de données**  
 Spécifiez le nom de la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 **Mot de passe**  
 Entrez le mot de passe pour la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur du gestionnaire de connexions SQL Server Compact Edition &#40;page Connexion&#41;](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager-editor-connection-page.md)  
  
  