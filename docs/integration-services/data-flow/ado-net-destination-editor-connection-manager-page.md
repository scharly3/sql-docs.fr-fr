---
title: "&#201;diteur de destination ADO NET (page Gestionnaire de connexions) | Microsoft Docs"
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
  - "sql13.dts.designer.adonetdest.connection.f1"
ms.assetid: a3b11286-32c8-40e1-8ae7-090e2590345a
caps.latest.revision: 31
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 31
---
# &#201;diteur de destination ADO NET (page Gestionnaire de connexions)
  Utilisez la page **Gestionnaire de connexions** de la boîte de dialogue **Éditeur de destination ADO NET** pour sélectionner la connexion [!INCLUDE[vstecado](../../includes/vstecado-md.md)] de la destination. Cette page vous permet également de sélectionner une table ou une vue à partir de la base de données.  
  
 Pour en savoir plus sur la destination ADO NET, consultez [ADO NET Destination](../../integration-services/data-flow/ado-net-destination.md).  
  
 **Pour ouvrir la page Gestionnaire de connexions**  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui possède la destination ADO NET.  
  
2.  Sous l’onglet **Flux de données**, double-cliquez sur la destination ADO NET.  
  
3.  Dans **l’Éditeur de destination ADO NET**, cliquez sur **Gestionnaire de connexions**.  
  
## Options statiques  
 **Gestionnaire de connexions**  
 Sélectionnez un gestionnaire de connexions existant dans la liste ou créez une connexion en cliquant sur **Nouveau**.  
  
 **Nouveau**  
 Créez un gestionnaire de connexions à l’aide de la boîte de dialogue **Configurer le gestionnaire de connexions ADO.NET**.  
  
 **Utiliser une table ou une vue**  
 Sélectionnez une table ou une vue existante dans la liste ou créez une table en cliquant sur **Nouvelle**.  
  
 **Nouveau**  
 Créez une table ou vue à l’aide de la boîte de dialogue **Créer une table**.  
  
> [!NOTE]  
>  Quand vous cliquez sur **Nouvelle**, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] génère une instruction CREATE TABLE par défaut, basée sur la source de données connectée. Cette instruction CREATE TABLE par défaut n'inclut pas l'attribut FILESTREAM, même si la table source inclut une colonne dans laquelle l'attribut FILESTREAM est déclaré. Pour exécuter un composant [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] avec l'attribut FILESTREAM, implémentez d'abord le stockage FILESTREAM sur la base de données de destination. Ajoutez ensuite l’attribut FILESTREAM à l’instruction CREATE TABLE dans la boîte de dialogue **Créer une table**. Pour plus d’informations, consultez [Données blob &#40;Binary Large Object&#41; &#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md).  
  
 **Aperçu**  
 Affichez un aperçu des résultats à l’aide de la boîte de dialogue **Visualiser les résultats de la requête**. L'aperçu peut afficher jusqu'à 200 lignes.  
  
 **Utiliser l'insertion en bloc le cas échéant**  
 Spécifiez s’il convient d’utiliser l’interface <xref:System.Data.SqlClient.SqlBulkCopy> pour améliorer les performances des opérations d’insertion en bloc.  
  
 Seuls les fournisseurs ADO.NET qui retournent un objet <xref:System.Data.SqlClient.SqlConnection> prennent en charge l’utilisation de l’interface <xref:System.Data.SqlClient.SqlBulkCopy>. Le fournisseur de données .NET pour SQL Server (SqlClient) retourne un objet <xref:System.Data.SqlClient.SqlConnection>, et un fournisseur personnalisé peut retourner un objet <xref:System.Data.SqlClient.SqlConnection>.  
  
 Le fournisseur de données .NET pour SQL Server (SqlClient) vous permet de vous connecter à [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)].  
  
 Si vous sélectionnez **Utiliser l’insertion en bloc le cas échéant** et affectez à l’option **Erreur** la valeur **Rediriger la ligne**, le lot de données que la destination redirige vers la sortie d’erreur peut inclure des lignes correctes. Pour plus d’informations sur la gestion des erreurs dans les opérations en bloc, consultez [Gestion des erreurs dans les données](../../integration-services/data-flow/error-handling-in-data.md). Pour plus d’informations sur l’option **Erreur**, consultez [Éditeur de destination ADO NET &#40;page Sortie d’erreur&#41;](../../integration-services/data-flow/ado-net-destination-editor-error-output-page.md).  
  
> [!NOTE]  
>  Si une table source [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou Sybase inclut une colonne d'identité, vous devez utiliser les tâches d'exécution de requêtes SQL pour exécuter une instruction SET IDENTITY_INSERT avant et après la destination ADO NET. La propriété de la colonne d'identité spécifie une valeur incrémentielle pour la colonne. L'instruction SET IDENTITY_INSERT autorise l'insertion de valeurs explicites dans la colonne d'identité. Pour exécuter les instructions CREATE TABLE et SET IDENTITY sur la même connexion de base de données, définissez la propriété **RetainSameConnection** du gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] avec la valeur **True**. En outre, utilisez le même gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] pour les tâches Exécuter SQL et la destination ADO NET.  
>   
>  Pour plus d’informations, consultez [SET IDENTITY_INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/set-identity-insert-transact-sql.md) et [IDENTITY &#40;Propriété&#41; &#40;Transact-SQL&#41;](../Topic/IDENTITY%20\(Property\)%20\(Transact-SQL\).md).  
  
## Ressources externes  
 Article technique sur sqlcat.com, traitant du [chargement rapide de données sur Microsoft Azure SQL Database](http://go.microsoft.com/fwlink/?LinkId=244333)  
  
## Voir aussi  
 [Éditeur de destination ADO NET &#40;page Mappages&#41;](../../integration-services/data-flow/ado-net-destination-editor-mappings-page.md)   
 [Éditeur de destination ADO NET &#40;page Sortie d’erreur&#41;](../../integration-services/data-flow/ado-net-destination-editor-error-output-page.md)   
 [Gestionnaire de connexions ADO.NET](../../integration-services/connection-manager/ado-net-connection-manager.md)   
 [Tache d'exécution de requêtes SQL](../../integration-services/control-flow/execute-sql-task.md)  
  
  