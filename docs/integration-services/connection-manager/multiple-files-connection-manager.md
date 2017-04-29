---
title: "Gestionnaire de connexions de fichiers multiples | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "dossiers [Integration Services], connexions"
  - "fichiers [Integration Services], connexions"
  - "Gestionnaire de connexions de fichiers multiples"
  - "gestionnaires de connexions [Integration Services], fichiers multiples"
  - "connexions [Integration Services], fichiers"
  - "connexions de fichiers multiples"
ms.assetid: 10bdc56e-c5cd-4ddb-b2f7-375fe57fe8b2
caps.latest.revision: 36
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 36
---
# Gestionnaire de connexions de fichiers multiples
  Un gestionnaire de connexions de fichiers multiples permet à un package de référencer des fichiers et dossiers existants ou de créer des fichiers ou dossiers au moment de l'exécution.  
  
> [!NOTE]  
>  Les tâches et composants de flux de données de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] n'utilisent pas le gestionnaire de connexions de fichiers multiples. Toutefois, vous pouvez utiliser ce gestionnaire de connexions dans la tâche de script ou le composant Script. Pour plus d’informations sur l’utilisation des gestionnaires de connexions avec la tâche de script, consultez [Connexion à des sources de données dans la tâche de script](../../integration-services/extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md). Pour plus d’informations sur l’utilisation des gestionnaires de connexions dans le composant Script, consultez [Connexion aux sources de données dans le composant Script](../../integration-services/extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md).  
  
## Types d'utilisations du gestionnaire de connexions de fichiers multiples  
 La propriété **FileUsageType** du gestionnaire de connexions de fichiers multiples indique la manière dont la connexion est utilisée. Le gestionnaire de connexions de fichiers multiples permet de créer des fichiers, de créer des dossiers, d'utiliser des fichiers existants et d'utiliser des dossiers existants.  
  
 Le tableau suivant répertorie les valeurs de **FileUsageType**.  
  
|Value|Description|  
|-----------|-----------------|  
|**0**|Le gestionnaire de connexions de fichiers multiples utilise un fichier existant.|  
|**1**|Le gestionnaire de connexions de fichiers multiples crée un fichier.|  
|**2**|Le gestionnaire de connexions de fichiers multiples utilise un dossier existant.|  
|**3**|Le gestionnaire de connexions de fichiers multiples crée un dossier.|  
  
## Configuration du gestionnaire de connexions de fichiers multiples  
 Quand vous ajoutez un gestionnaire de connexions de fichiers multiples à un package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée un gestionnaire de connexions qui sera converti en connexion de fichiers multiples au moment de l’exécution, définit les propriétés de la connexion de fichiers multiples et ajoute la connexion de fichiers multiples à la collection **Connections** du package.  
  
 La propriété **ConnectionManagerType** du gestionnaire de connexions a la valeur **MULTIFILE**.  
  
 Vous pouvez configurer un gestionnaire de connexions de fichiers multiples de plusieurs manières :  
  
-   Spécifiez le type d'utilisation des fichiers et des dossiers.  
  
-   Spécifiez les fichiers et les dossiers.  
  
-   Si vous utilisez plusieurs fichiers ou dossiers, indiquez l'ordre d'accès des fichiers et dossiers.  
  
 Si le gestionnaire de connexions de fichiers multiples référence plusieurs fichiers et dossiers, les chemins d'accès aux fichiers et dossiers sont séparés par une barre verticale (|). La propriété **ConnectionString** du gestionnaire de connexions utilise le format suivant :  
  
 \<*chemin*>|\<*chemin*>  
  
 Vous pouvez également spécifier plusieurs fichiers ou dossiers en utilisant des caractères génériques. Par exemple, pour référencer tous les fichiers texte du lecteur C, la valeur de la propriété **ConnectionString**peut être définie sur C:\\*.txt.  
  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)], consultez [Référence de l’interface utilisateur de la boîte de dialogue Ajouter un gestionnaire de connexions de fichiers](../../integration-services/connection-manager/add-file-connection-manager-dialog-box-ui-reference.md).  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programmation, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> et [Ajout de connexions par programmation](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
  