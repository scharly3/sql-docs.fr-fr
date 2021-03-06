# [Vue d’ensemble](xml-data-sql-server.md)  
# [Type et colonnes de données XML](xml-data-type-and-columns-sql-server.md)  
## [Comparer du XML typé et du XML non typé](compare-typed-xml-to-untyped-xml.md)  
## [Créer des instances de données XML](create-instances-of-xml-data.md)  
## [Créer des variables et des colonnes de type de données XML](create-xml-data-type-variables-and-columns.md)  
## [Transformer les colonnes existantes en colonnes XML](change-existing-columns-to-xml-columns.md)  
## [Charger des données XML](load-xml-data.md)  
## [Créer des vues sur les colonnes XML](create-views-over-xml-columns.md)  
## [Utiliser des données XML dans les colonnes calculées](use-xml-in-computed-columns.md)  
## [Récupérer et interroger des données XML](retrieve-and-query-xml-data.md)  
## [Ajouter des espaces de noms aux requêtes avec WITH XMLNAMESPACES](add-namespaces-to-queries-with-with-xmlnamespaces.md)  
## [Promouvoir les valeurs XML les plus fréquentes à l’aide de colonnes calculées](promote-frequently-used-xml-values-with-computed-columns.md)  
## [Définir la sérialisation des données XML](define-the-serialization-of-xml-data.md)  
## [Utiliser la recherche en texte intégral avec des colonnes XML](use-full-text-search-with-xml-columns.md)  
## [Ajouter la logique métier aux données XML](add-business-logic-to-xml-data.md)  
## [Utiliser des données XML dans les applications](use-xml-data-in-applications.md)  
# [Index XML](xml-indexes-sql-server.md)  
## [Créer des index XML](create-xml-indexes.md)  
## [Modifier les index XML](modify-xml-indexes.md)  
## [Supprimer des index XML](drop-xml-indexes.md)  
## [Index XML sélectifs (SXI)](selective-xml-indexes-sxi.md)  
## [Spécifier les chemins d’accès et les indicateurs d’optimisation des index XML sélectifs](specify-paths-and-optimization-hints-for-selective-xml-indexes.md)  
## [Créer, modifier ou supprimer des index XML sélectifs](create-alter-and-drop-selective-xml-indexes.md)  
## [Créer, modifier ou supprimer des index XML secondaires sélectifs](create-alter-and-drop-secondary-selective-xml-indexes.md)  
# [Collections de schémas XML](xml-schema-collections-sql-server.md)  
## [Référencer la collection de schémas XML intégrée (sys)](reference-the-built-in-xml-schema-collection-sys.md)  
## [Afficher une collection de schémas XML stockée](view-a-stored-xml-schema-collection.md)  
## [Accorder des autorisations sur une collection de schémas XML](grant-permissions-on-an-xml-schema-collection.md)  
## [Révoquer des autorisations sur une collection de schémas XML](revoke-permissions-on-an-xml-schema-collection.md)  
## [Refuser des autorisations sur une collection de schémas XML](deny-permissions-on-an-xml-schema-collection.md)  
## [Prétraiter un schéma pour fusionner des schémas inclus](preprocess-a-schema-to-merge-included-schemas.md)  
## [Spécifications et limitations relatives aux collections de schémas XML sur le serveur](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
### [Formes canoniques et restrictions de modèle](canonical-forms-and-pattern-restrictions.md)  
### [Composants génériques et validation de contenu](wildcard-components-and-content-validation.md)  
### [Élément <xsd:redefine>](the-xsd-redefine-element.md)  
### [Type xs:QName](the-xs-qname-type.md)  
### [Valeurs pour les déclarations <xsd:simpleType>](values-for-xsd-simpletype-declarations.md)  
### [Facettes d’énumération](enumeration-facets.md)  
### [Type mixte et contenu simple](mixed-type-and-simple-content.md)  
### [Collections de schémas XML volumineuses et conditions de mémoire insuffisante](large-xml-schema-collections-and-out-of-memory-conditions.md)  
### [Modèles de contenu non déterministes](non-deterministic-content-models.md)  
### [Contrainte d’attribution de particule unique](unique-particle-attribution-constraint.md)  
# [FOR XML](for-xml-sql-server.md)  
## [Syntaxe de base de la clause FOR XML](basic-syntax-of-the-for-xml-clause.md)  
## [Caractères non valides et règles d’échappement](invalid-characters-and-escape-rules.md)  
## [Utiliser le mode RAW avec FOR XML](use-raw-mode-with-for-xml.md)  
### [Exemple : récupération des informations de modèle de produit au format XML](example-retrieving-product-model-information-as-xml.md)  
### [Exemple : spécification de XSINIL avec la directive ELEMENTS](example-specifying-xsinil-with-the-elements-directive.md)  
### [Exemple : demande de schémas comme résultats à l'aide des options XMLDATA et XMLSCHEMA](example-requesting-schemas-as-results-with-the-xmldata-and-xmlschema-options.md)  
### [Exemple : extraction de données binaires](example-retrieving-binary-data.md)  
### [Exemple : attribution d’un nouveau nom à l’élément <row>](example-renaming-the-row-element.md)  
### [Exemple : spécification d’un élément racine pour les données XML générées par FOR XML](example-specifying-a-root-element-for-the-xml-generated-by-for-xml.md)  
### [Exemple : interrogation de colonnes de type XML](example-querying-xmltype-columns.md)  
## [Utiliser le mode AUTO avec FOR XML](use-auto-mode-with-for-xml.md)  
### [Utiliser l’option BINARY BASE64](use-the-binary-base64-option.md)  
### [Heuristique du mode AUTO permettant de définir la forme des données XML renvoyées](auto-mode-heuristics-in-shaping-returned-xml.md)  
### [Exemples : utilisation du mode AUTO](examples-using-auto-mode.md)  
## [Utiliser le mode EXPLICIT avec FOR XML](use-explicit-mode-with-for-xml.md)  
### [Exemple : extraction d’informations sur les employés](example-retrieving-employee-information.md)  
### [Exemple : spécification de la directive ELEMENT](example-specifying-the-element-directive.md)  
### [Exemple : spécification de la directive ELEMENTXSINIL](example-specifying-the-elementxsinil-directive.md)  
### [Exemple : construction de frères à l'aide du mode EXPLICIT](example-constructing-siblings-with-explicit-mode.md)  
### [Exemple : spécification des directives ID et IDREF](example-specifying-the-id-and-idref-directives.md)  
### [Exemple : spécification des directives ID et IDREFS](example-specifying-the-id-and-idrefs-directives.md)  
### [Exemple : spécification de la directive HIDE](example-specifying-the-hide-directive.md)  
### [Exemple : spécification de la directive ELEMENT et de l'encodage d'entité](example-specifying-the-element-directive-and-entity-encoding.md)  
### [Exemple : spécification de la directive CDATA](example-specifying-the-cdata-directive.md)  
### [Exemple : spécification de la directive XMLTEXT](example-specifying-the-xmltext-directive.md)  
## [Utiliser le mode PATH avec FOR XML](use-path-mode-with-for-xml.md)  
### [Colonnes sans nom](columns-without-a-name.md)  
### [Colonnes avec nom](columns-with-a-name.md)  
### [Colonnes avec un nom spécifié sous la forme d'un caractère générique](columns-with-a-name-specified-as-a-wildcard-character.md)  
### [Colonnes avec le nom d’un test de nœud XPath](columns-with-the-name-of-an-xpath-node-test.md)  
### [Noms de colonnes avec le chemin d’accès spécifié sous la forme data()](column-names-with-the-path-specified-as-data.md)  
### [Colonnes contenant une valeur NULL par défaut](columns-that-contain-a-null-value-by-default.md)  
### [Prise en charge d'espace de noms en mode PATH](namespace-support-in-path-mode.md)  
### [Exemples : utilisation du mode PATH](examples-using-path-mode.md)  
## [Directive TYPE dans les requêtes FOR XML](type-directive-in-for-xml-queries.md)  
## [Générer du code XML à partir d’ensembles de lignes avec FOR XML](generate-xml-from-rowsets-with-for-xml.md)  
## [Utiliser des résultats FOR XML dans le code de l’application](use-for-xml-results-in-application-code.md)  
## [Utiliser des requêtes FOR XML imbriquées](use-nested-for-xml-queries.md)  
### [Comparaison de la requête FOR XML et de la requête FOR XML imbriquée](for-xml-query-compared-to-nested-for-xml-query.md)  
### [Générer des frères à l’aide d’une requête imbriquée en mode AUTO](generate-siblings-with-a-nested-auto-mode-query.md)  
### [Utiliser des requêtes FOR XML imbriquées dans ASP.NET](use-nested-for-xml-queries-in-asp-net.md)  
### [Façonner des données XML avec des requêtes FOR XML imbriquées](shape-xml-with-nested-for-xml-queries.md)  
## [Générer des éléments pour des valeurs NULL avec le paramètre XSINIL](generate-elements-for-null-values-with-the-xsinil-parameter.md)  
## [Prise en charge de FOR XML pour différents types de données SQL Server](for-xml-support-for-various-sql-server-data-types.md)  
### [Prise en charge de FOR XML pour le type de données XML](for-xml-support-for-the-xml-data-type.md)  
### [Prise en charge de FOR XML pour les types de données définis par l’utilisateur (UDT)](for-xml-support-for-the-user-defined-data-types-udt.md)  
### [Prise en charge de FOR XML pour les types de données string](for-xml-support-for-string-data-types.md)  
### [Prise en charge de FOR XML pour le type de données timestamp](for-xml-support-for-the-timestamp-data-type.md)  
## [Générer un schéma XSD inline](generate-an-inline-xsd-schema.md)  
## [Générer un schéma XDR inline](generate-an-inline-xdr-schema.md)  
# [OPENXML](openxml-sql-server.md)  
## [Exemples : utilisation de OPENXML](examples-using-openxml.md)  
## [Spécifier des métapropriétés dans OPENXML](specify-metaproperties-in-openxml.md)  
## [Procédures stockées système XML](xml-system-stored-procedures.md)  
## [Utiliser les méthodes value() et nodes() avec OPENXML](use-the-value-and-nodes-methods-with-openxml.md)  
