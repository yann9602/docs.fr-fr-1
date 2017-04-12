---
title: "Introduction à LINQ en Visual Basic | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- queries [LINQ in Visual Basic], about LINQ in Visual Basic queries
- query execution [LINQ in Visual Basic]
- range variables
- LINQ [Visual Basic]
- LINQ [Visual Basic], about LINQ in Visual Basic
- query expressions [LINQ in Visual Basic]
- LINQ
- deferred execution
- iteration variables
ms.assetid: 3047d86e-0d49-40e2-928b-dc02e46c7984
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e1343b06089df63beb73cbb27a38de396f5cb6c8
ms.lasthandoff: 03/13/2017

---
# <a name="introduction-to-linq-in-visual-basic"></a>Introduction à LINQ dans Visual Basic
LINQ (Language-Integrated Query) ajoute des fonctions de requête à [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] et fournit des fonctions simples et puissantes permettant de travailler avec tous les types de données. Au lieu d'envoyer une requête à une base de données à des fins de traitement ou d'utiliser une syntaxe de requête différente pour chaque type de données que vous recherchez, LINQ introduit des requêtes dans le cadre du langage [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]. Il utilise une syntaxe unifiée indépendamment du type de données.  
  
 LINQ vous permet d’interroger des données à partir d’une base de données SQL Server, XML, tableaux en mémoire et les collections, [!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)] jeux de données ou d’autres données locales ou distantes source qui prend en charge LINQ. Vous pouvez faire toutes ces choses avec les éléments de langage [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] communs. Comme vos requêtes sont écrites en langage [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], vos résultats de requête sont retournés en tant qu'objets fortement typés. Ces objets prennent en charge IntelliSense, qui vous permet d'écrire du code plus rapidement et d'intercepter les erreurs dans vos requêtes au moment de la compilation plutôt qu'au moment de l'exécution. Les requêtes LINQ peuvent être utilisées comme source de requêtes supplémentaires pour affiner les résultats. Elles peuvent également être liées à des contrôles pour que les utilisateurs puissent afficher et modifier facilement vos résultats de requête.  
  
 Par exemple, l’exemple de code suivant affiche une requête LINQ qui retourne une liste de clients à partir d’une collection et les regroupe en fonction de leur emplacement.  
  
 [!code-vb[VbVbalrIntroToLINQ n °&1;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_1.vb)]  
  
 Cette rubrique comprend des informations sur les sujets suivants :  
  
-   [Exécution des exemples](#RunningtheExamples)  
  
-   [Fournisseurs LINQ](#LINQProviders)  
  
-   [Structure d’une requête LINQ](#StructureOfALINQQuery)  
  
-   [Opérateurs de requête LINQ de Visual Basic](#VisualBasicLINQQueryOperators)  
  
-   [Connexion à une base de données à l’aide de LINQ to SQL](#ConnectingToADatabase)  
  
-   [Fonctionnalités Visual Basic prenant en charge LINQ](#VisualBasicFeaturesThatSupportLINQ)  
  
-   [Exécution de requête différée et immédiate](#QueryExecution)  
  
-   [XML en Visual Basic](#XMLInVisualBasic)  
  
-   [Ressources connexes](#RelatedResources)  
  
-   [Comment et les rubriques de procédure pas à pas](#HowToAndWalkthroughTopics)  
  
##  <a name="RunningtheExamples"></a>Exécution des exemples  
 Pour exécuter les exemples de l'introduction et de la section « Structure d'une requête LINQ », incluez le code suivant qui retourne les listes de clients et de commandes.  
  
 [!code-vb[VbVbalrIntroToLINQ&#31;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_2.vb)]  
  
##  <a name="LINQProviders"></a>Fournisseurs LINQ  
 A *fournisseur LINQ* mappe votre [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] requêtes LINQ pour la source de données interrogée. Quand vous écrivez une requête LINQ, le fournisseur prend cette requête et la traduit en commandes que la source de données sera en mesure d'exécuter. Le fournisseur convertit également des données de la source en objets qui composent votre résultat de la requête. Enfin, il convertit des objets en données quand vous envoyez des mises à jour à la source de données.  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] inclut les fournisseurs LINQ suivants.  
  
|Fournisseur|Description|  
|---|---|  
|LINQ to Objects|Le fournisseur LINQ to Objects vous permet d’interroger des collections et des tableaux en mémoire. Si un objet prend en charge l' <xref:System.Collections.IEnumerable>ou de <xref:System.Collections.Generic.IEnumerable%601>l’interface, le fournisseur LINQ to Objects vous permet d’interroger de celui-ci.</xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.IEnumerable><br /><br /> Vous pouvez activer le fournisseur LINQ to Objects en important le <xref:System.Linq>espace de noms qui est importé par défaut pour toutes les [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] projets.</xref:System.Linq><br /><br /> Pour plus d’informations sur le fournisseur LINQ to Objects, consultez [LINQ to Objects](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9).|  
|LINQ to SQL|Le fournisseur LINQ to SQL vous permet d'interroger et de modifier des données dans une base de données SQL Server. Cela facilite le mappage du modèle objet d'une application aux tables et objets d'une base de données.<br /><br /> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] facilite l'utilisation de LINQ to SQL en incluant le Concepteur Objet Relationnel (Concepteur O/R). Ce concepteur est utilisé pour créer un modèle objet dans une application qui effectue un mappage aux objets d'une base de données. Le Concepteur O/R également fournit la fonctionnalité permettant de mapper des procédures stockées et des fonctions à la <xref:System.Data.Linq.DataContext>objet qui gère la communication avec la base de données et stocke l’état de contrôles d’accès concurrentiel optimiste.</xref:System.Data.Linq.DataContext><br /><br /> Pour plus d’informations sur le fournisseur LINQ to SQL, consultez la page [LINQ to SQL](https://msdn.microsoft.com/library/bb386976). Pour plus d’informations sur le concepteur objet/relationnel, consultez [LINQ to SQL Tools dans Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).|  
|LINQ to XML|Le fournisseur LINQ to XML vous permet d'interroger et de modifier du code XML. Vous pouvez modifier du code XML en mémoire ou le charger à partir d'un fichier, mais également l'enregistrer dans un fichier.<br /><br /> En outre, le fournisseur LINQ to XML active des littéraux XML et des propriétés d'axe XML qui vous permettent d'écrire directement du code XML dans votre code [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]. Pour plus d’informations, consultez [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md).|  
|LINQ to DataSet|Le fournisseur LINQ to DataSet vous permet d’interroger et mise à jour les données dans un [!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)] jeu de données. Vous pouvez ajouter la puissance de LINQ aux applications qui utilisent des groupes de données afin de simplifier et d'étendre vos capacités de requête, d'agrégation et de mise à jour des données dans votre dataset.<br /><br /> Pour plus d’informations, consultez [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17).|  
  
##  <a name="StructureOfALINQQuery"></a>Structure d’une requête LINQ  
 Une requête LINQ, souvent appelé un *expression de requête*, se compose d’une combinaison de clauses de requête qui identifient les sources de données et les variables d’itération pour la requête. Une expression de requête peut également inclure des instructions de tri, de filtrage, de regroupement et de jonction ou des calculs applicables aux données sources. La syntaxe de l'expression de requête ressemble à la syntaxe de SQL ; par conséquent, une grande partie de cette syntaxe vous semblera familière.  
  
 Une expression de requête commence par une clause `From`. Cette clause identifie les données sources d'une requête et les variables utilisées pour faire individuellement référence à chaque élément des données sources. Ces variables sont appelées *variables de plage* ou *variables d’itération*. La clause `From` est nécessaire pour une requête, à l'exception des requêtes `Aggregate`, où la clause `From` est facultative. Après avoir identifié la portée et la source de la requête dans les clauses `From` ou `Aggregate`, vous pouvez inclure toute combinaison de clauses de requête pour affiner la requête. Pour plus d'informations sur les clauses de requête, consultez la section Opérateurs de requête LINQ [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] plus loin dans cette rubrique. Par exemple, la requête suivante identifie une collection de sources de données client comme variable `customers` et une variable d'itération appelée `cust`.  
  
 [!code-vb[VbVbalrIntroToLINQ n °&2;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_3.vb)]  
  
 Cet exemple représente une requête valide en elle-même ; toutefois, la requête gagne en puissance quand vous ajoutez davantage de clauses de requête pour affiner le résultat. Par exemple, vous pouvez ajouter une clause `Where` pour filtrer le résultat en fonction d'une ou plusieurs valeurs. Les expressions de requête forment une ligne unique de code ; il vous suffit d'ajouter des clauses de requête supplémentaires à la fin de la requête. Vous pouvez décomposer une requête en plusieurs lignes de texte pour améliorer la lisibilité à l'aide du trait de soulignement (_), un caractère de continuation de ligne. L'exemple de code suivant illustre une requête qui inclut une clause `Where`.  
  
 [!code-vb[VbVbalrIntroToLINQ n °&3;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_4.vb)]  
  
 Autre clause de requête performante, la clause `Select` vous permet de retourner uniquement des champs sélectionnés de la source de données. Les requêtes LINQ retournent des collections énumérables d'objets fortement typés. Une requête peut retourner une collection de types anonymes ou nommés. Vous pouvez utiliser la clause `Select` pour retourner uniquement un champ de la source de données. Dans ce cas, le type de la collection retournée est le type de ce champ unique. Vous pouvez également utiliser la clause `Select` pour retourner plusieurs champs de la source de données. Dans ce cas, le type de la collection retournée est un nouveau type anonyme. Vous pouvez également faire correspondre les champs retournés par la requête aux champs d'un type nommé spécifié. L’exemple de code suivant affiche une expression de requête qui retourne une collection de types anonymes dont les membres sont remplis des données des champs sélectionnés de la source de données.  
  
 [!code-vb[VbVbalrIntroToLINQ n °&4;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_5.vb)]  
  
 Les requêtes LINQ peuvent également être utilisées pour combiner plusieurs sources de données et retourner un résultat unique. Cette opération peut être effectuée à l'aide d'une ou plusieurs clauses `From` ou en utilisant les clauses de requête `Join` ou `Group Join`. L’exemple de code suivant illustre une expression de requête qui combine des données de client et de commande et retourne une collection de types anonymes contenant ces deux types de données.  
  
 [!code-vb[VbVbalrIntroToLINQ n °&5;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_6.vb)]  
  
 Vous pouvez utiliser la clause `Group Join` pour créer un résultat de requête hiérarchique contenant une collection d'objets customer. Chaque objet customer possède une propriété contenant une collection de toutes les commandes de ce client. L'exemple de code suivant affiche une expression de requête qui combine des données client/commande sous forme de résultat hiérarchique et retourne une collection de types anonymes. La requête retourne un type qui inclut une propriété `CustomerOrders` contenant une collection de données de commande pour le client. Il inclut également une propriété `OrderTotal` qui contient la somme des totaux pour toutes les commandes de ce client. (Cette requête est équivalente à une JOINTURE EXTERNE GAUCHE.)  
  
 [!code-vb[VbVbalrIntroToLINQ n °&6;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_7.vb)]  
  
 Il existe plusieurs opérateurs de requête LINQ supplémentaires qui vous permettent de créer des expressions de requête puissantes. La section suivante de cette rubrique présente les différentes clauses de requête que vous pouvez inclure dans une expression de requête. Pour plus d’informations sur [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] clauses de requête, consultez [requêtes](../../../../visual-basic/language-reference/queries/queries.md).  
  
##  <a name="VisualBasicLINQQueryOperators"></a>Opérateurs de requête LINQ de Visual Basic  
 Les classes dans le <xref:System.Linq>espace de noms et les autres espaces de noms qui prennent en charge les requêtes LINQ incluent des méthodes que vous pouvez appeler pour créer et affiner les requêtes en fonction des besoins de votre application.</xref:System.Linq> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] inclut des mots clés pour les clauses de requête les plus courantes, comme indiqué dans le tableau suivant.  
  
|Terme|Définition|  
|---|---|  
|[From (clause)](../../../../visual-basic/language-reference/queries/from-clause.md)|Une requête doit commencer par une clause `From` ou `Aggregate`. Une clause `From` spécifie une collection de sources et une variable d'itération pour une requête. Exemple :<br /><br /> [!code-vb[VbVbalrIntroToLINQ&#7;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_8.vb)]|  
|[Select (clause)](../../../../visual-basic/language-reference/queries/select-clause.md)|Facultatif. Déclare un jeu de variables d'itération pour une requête. Exemple :<br /><br /> [!code-vb[VbVbalrIntroToLINQ n °&8;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_9.vb)]<br /><br /> Si une clause `Select` n'est pas spécifiée, les variables d'itération de la requête se composent des variables d'itération spécifiées par la clause `From` ou `Aggregate`.|  
|[Where (clause)](../../../../visual-basic/language-reference/queries/where-clause.md)|Facultatif. Spécifie une condition de filtrage pour une requête. Exemple :<br /><br /> [!code-vb[VbVbalrIntroToLINQ&#9;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_10.vb)]|  
|[Order By (clause)](../../../../visual-basic/language-reference/queries/order-by-clause.md)|Facultatif. Spécifie l'ordre de tri des colonnes dans une requête. Exemple :<br /><br /> [!code-vb[VbVbalrIntroToLINQ&#10;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_11.vb)]|  
|[Join (clause)](../../../../visual-basic/language-reference/queries/join-clause.md)|Facultatif. Combine deux collections en une collection unique. Exemple :<br /><br /> [!code-vb[VbVbalrIntroToLINQ&#11;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_12.vb)]|  
|[Group By (clause)](../../../../visual-basic/language-reference/queries/group-by-clause.md)|Facultatif. Regroupe les éléments d'un résultat de requête. Peut être utilisée pour appliquer des fonctions d'agrégation à chaque groupe. Exemple :<br /><br /> [!code-vb[VbVbalrIntroToLINQ&#12;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_13.vb)]|  
|[Group Join (clause)](../../../../visual-basic/language-reference/queries/group-join-clause.md)|Facultatif. Combine deux collections en une collection hiérarchique unique. Exemple :<br /><br /> [!code-vb[VbVbalrIntroToLINQ&#13;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_14.vb)]|  
|[Aggregate (clause)](../../../../visual-basic/language-reference/queries/aggregate-clause.md)|Une requête doit commencer par une clause `From` ou `Aggregate`. Une clause `Aggregate` applique une ou plusieurs fonctions d'agrégation à une collection. Par exemple, vous pouvez utiliser la clause `Aggregate` pour calculer une somme de tous les éléments retournés par une requête.<br /><br /> [!code-vb[VbVbalrIntroToLINQ&#14;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_15.vb)]<br /><br /> Vous pouvez également utiliser la clause `Aggregate` pour modifier une requête. Par exemple, vous pouvez utiliser la clause `Aggregate` pour effectuer un calcul sur une collection de requêtes connexe.<br /><br /> [!code-vb[VbVbalrIntroToLINQ&#15;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_16.vb)]|  
|[Let (clause)](../../../../visual-basic/language-reference/queries/let-clause.md)|Facultatif. Calcule une valeur et l'assigne à une nouvelle variable dans la requête. Exemple :<br /><br /> [!code-vb[VbVbalrIntroToLINQ&#16;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_17.vb)]|  
|[Distinct (clause)](../../../../visual-basic/language-reference/queries/distinct-clause.md)|Facultatif. Restreint les valeurs de la variable d'itération actuelle pour éliminer les valeurs en double dans les résultats de la requête. Exemple :<br /><br /> [!code-vb[VbVbalrIntroToLINQ&#17;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_18.vb)]|  
|[Skip (clause)](../../../../visual-basic/language-reference/queries/skip-clause.md)|Facultatif. Ignore un nombre spécifié d'éléments dans une collection, puis retourne les éléments restants. Exemple :<br /><br /> [!code-vb[VbVbalrIntroToLINQ&#18;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_19.vb)]|  
|[Skip While (clause)](../../../../visual-basic/language-reference/queries/skip-while-clause.md)|Facultatif. Ignore les éléments d'une collection tant qu'une condition spécifiée a la valeur `true`, puis retourne les éléments restants. Exemple :<br /><br /> [!code-vb[VbVbalrIntroToLINQ n °&19;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_20.vb)]|  
|[Take (clause)](../../../../visual-basic/language-reference/queries/take-clause.md)|Facultatif. Retourne un nombre spécifié d'éléments contigus à partir du début d'une collection. Exemple :<br /><br /> [!code-vb[VbVbalrIntroToLINQ&#20;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_21.vb)]|  
|[Take While (clause)](../../../../visual-basic/language-reference/queries/take-while-clause.md)|Facultatif. Inclut les éléments d'une collection tant qu'une condition spécifiée a la valeur `true` et ignore les éléments restants. Exemple :<br /><br /> [!code-vb[VbVbalrIntroToLINQ n °&21;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_22.vb)]|  
  
 Pour plus d’informations sur [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] clauses de requête, consultez [requêtes](../../../../visual-basic/language-reference/queries/queries.md).  
  
 Vous pouvez utiliser des fonctionnalités de requête LINQ supplémentaires en appelant des membres des types énumérables et requêtables fournis par LINQ. Vous pouvez utiliser ces fonctions supplémentaires en appelant un opérateur de requête particulier sur le résultat d'une expression de requête. Par exemple, le code suivant montre comment utiliser le <xref:System.Linq.Enumerable.Union%2A>méthode pour combiner les résultats de deux requêtes dans le résultat d’une requête.</xref:System.Linq.Enumerable.Union%2A> Il utilise le <xref:System.Linq.Enumerable.ToList%2A>méthode pour retourner le résultat de la requête sous forme de liste générique.</xref:System.Linq.Enumerable.ToList%2A>  
  
 [!code-vb[VbVbalrIntroToLINQ&#22;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_23.vb)]  
  
 Pour plus d’informations sur les fonctions LINQ supplémentaires, consultez la page [vue d’ensemble des opérateurs de requête Standard](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).  
  
##  <a name="ConnectingToADatabase"></a>Connexion à une base de données à l’aide de LINQ to SQL  
 Dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], vous identifiez les objets de base de données SQL Server, comme les tables, vues et procédures stockées, auxquels vous souhaitez accéder en utilisant un fichier LINQ to SQL. Un fichier LINQ to SQL possède une extension .dbml.  
  
 Lorsque vous avez une connexion valide à une base de données SQL Server, vous pouvez ajouter un **Classes LINQ to SQL** modèle d’élément à votre projet. Le Concepteur Objet Relationnel (Concepteur O/R) s'affiche alors. Le Concepteur O/R vous permet de faire glisser les éléments que vous souhaitez accéder dans votre code à partir de la **Explorateur de serveurs**/**Database Explorer** sur l’aire du concepteur. Le fichier LINQ to SQL ajoute un <xref:System.Data.Linq.DataContext>objet à votre projet.</xref:System.Data.Linq.DataContext> Cet objet inclut des propriétés et des collections pour les tables et vues auxquelles vous souhaitez accéder, et aux méthodes des procédures stockées que vous souhaitez appeler. Après avoir enregistré vos modifications dans le fichier LINQ to SQL (.dbml), vous pouvez accéder à ces objets dans votre code en référençant le <xref:System.Data.Linq.DataContext>objet défini par le Concepteur O/R.</xref:System.Data.Linq.DataContext> Le <xref:System.Data.Linq.DataContext>objet pour votre projet est nommé d’après le nom de votre fichier LINQ to SQL.</xref:System.Data.Linq.DataContext> Par exemple, un fichier LINQ to SQL nommé Northwind.dbml créera un <xref:System.Data.Linq.DataContext>objet nommé `NorthwindDataContext`.</xref:System.Data.Linq.DataContext>  
  
 Pour obtenir des exemples des instructions détaillées, consultez [Comment : interroger une base de données](../../../../visual-basic/programming-guide/language-features/linq/how-to-query-a-database-by-using-linq.md) et [Comment : appeler une procédure stockée](../../../../visual-basic/programming-guide/language-features/linq/how-to-call-a-stored-procedure-by-using-linq.md).  
  
##  <a name="VisualBasicFeaturesThatSupportLINQ"></a>Fonctionnalités de Visual Basic qui prennent en charge LINQ  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] inclut d'autres fonctionnalités notables qui facilitent l'utilisation de LINQ et réduisent la quantité de code que vous devez écrire pour effectuer des requêtes LINQ. Notamment :  
  
-   **Les types anonymes**, qui permettent de créer un nouveau type basé sur un résultat de requête.  
  
-   **Variables implicitement typées**, qui permettent de différer la spécification d’un type et laisser le compilateur déduire le type selon le résultat de la requête.  
  
-   **Méthodes d’extension**, vous permettent d’étendre un type existant avec vos propres méthodes sans modifier le type lui-même.  
  
 Pour plus d’informations, consultez [fonctionnalités Visual Basic que LINQ prise en charge](../../../../visual-basic/programming-guide/concepts/linq/features-that-support-linq.md).  
  
##  <a name="QueryExecution"></a>Exécution de requête différée et immédiate  
 L'exécution d'une requête est distincte de sa création. Après avoir créé une requête, son exécution est déclenchée par un mécanisme distinct. Une requête peut être exécutée dès qu’elle est définie (*l’exécution immédiate*), ou la définition peut être stockée et la requête peut être exécutée ultérieurement (*exécution différée*).  
  
 Par défaut, quand vous créez une requête, cette dernière ne s'exécute pas immédiatement. À la place, la définition de la requête est stockée dans la variable utilisée pour référencer le résultat de la requête. Quand vous accédez à la variable de résultat de la requête ultérieurement dans le code, par exemple, dans une boucle `For…Next`, la requête est exécutée. Ce processus est appelé *exécution différée*.  
  
 Les requêtes peuvent également être exécutées lorsqu’elles sont définies, ce qui est appelé *exécution*. Vous pouvez déclencher l'exécution immédiate en appliquant une méthode qui requiert l'accès aux éléments individuels du résultat de la requête. L'inclusion d'une fonction d'agrégation, telle que `Count`, `Sum`, `Average`, `Min` ou `Max` peut engendrer un tel résultat. Pour plus d’informations sur les fonctions d’agrégation, consultez [Clause Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 L'utilisation de la méthode `ToList` ou `ToArray` force également l'exécution immédiate. Cela peut être utile quand vous souhaitez exécuter immédiatement la requête et mettre en cache les résultats. Pour plus d’informations sur ces méthodes, consultez [convertir les Types de données](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).  
  
 Pour plus d’informations sur l’exécution des requêtes, consultez [écrire votre première requête LINQ](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
##  <a name="XMLInVisualBasic"></a>XML en Visual Basic  
 Les fonctionnalités XML de [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] incluent des littéraux XML et des propriétés d'axe XML, qui facilitent la création, l'accès, l'interrogation et la modification du XML dans votre code. Les littéraux XML vous permettent d'écrire directement en XML dans votre code. Le compilateur Visual Basic traite le XML comme un objet de donnée de première classe.  
  
 L'exemple de code suivant montre comment créer un élément XML, accéder à ses sous-éléments et attributs, et interroger son contenu à l'aide de LINQ.  
  
 [!code-vb[VbXmlSamples n °&8;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/introduction-to-linq_24.vb)]  
  
 Pour plus d’informations, consultez [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md).  
  
##  <a name="RelatedResources"></a>Ressources connexes  
  
|Rubrique|Description|  
|---|---|  
|[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)|Décrit les fonctionnalités XML de [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] qui peuvent être interrogées et qui vous permettent d'inclure du XML sous forme d'objets de données de première classe dans votre code [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].|  
|[Requêtes](../../../../visual-basic/language-reference/queries/queries.md)|Fournit des informations de référence sur les clauses de requête disponibles dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].|  
|[LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)|Inclut des informations générales, un guide de programmation et des exemples de requêtes LINQ.|  
|[LINQ to SQL](https://msdn.microsoft.com/library/bb386976)|Inclut des informations générales, un guide de programmation et des exemples de LINQ to SQL.|  
|[LINQ to Objects](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9)|Inclut des informations générales, un guide de programmation et des exemples de LINQ to Objects.|  
|[LINQ to ADO.NET (page de portail)](http://msdn.microsoft.com/library/dd7d3c6a-ff98-47e9-a1a7-2d4cfc42d150)|Inclut des liens vers des informations générales, un guide de programmation et des exemples de LINQ to [!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)].|  
|[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13)|Inclut des informations générales, un guide de programmation et des exemples de LINQ to XML.|  
  
##  <a name="HowToAndWalkthroughTopics"></a>Comment et les rubriques de procédure pas à pas  
 [Comment : interroger une base de données](how-to-query-a-database-by-using-linq.md)  
  
 [Comment : appeler une procédure stockée](how-to-call-a-stored-procedure-by-using-linq.md)  
  
 [Comment : modifier des données dans une base de données](how-to-modify-data-in-a-database-by-using-linq.md)  
  
 [Comment : combiner des données avec des jointures](how-to-combine-data-with-linq-by-using-joins.md)  
  
 [Comment : trier les résultats de la requête](how-to-sort-query-results-by-using-linq.md)  
  
 [Comment : filtrer les résultats de la requête](how-to-filter-query-results-by-using-linq.md)  
  
 [Comment : Count, Sum ou moyenne des données](how-to-count-sum-or-average-data-by-using-linq.md)  
  
 [Comment : rechercher la valeur minimale ou maximale dans un résultat de requête](how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)  
  
 [Comment : assigner des procédures stockées pour effectuer des mises à jour, insertions et suppressions (Concepteur O/R)](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)  
  
## <a name="featured-book-chapters"></a>Chapitres proposés  
 [Chapitre 17 : LINQ](http://go.microsoft.com/fwlink/?LinkId=195277) dans [de programmation Visual Basic 2008](http://go.microsoft.com/fwlink/?LinkId=195383)  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)   
 [Vue d’ensemble de LINQ to XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)   
 [LINQ to DataSet présentation](http://msdn.microsoft.com/library/dc20a8fb-03f6-4b68-9c2b-7f7299e3070b)   
 [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)  
 [LINQ to SQL Tools dans Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)   
 [Méthodes DataContext (Concepteur O/R)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)
