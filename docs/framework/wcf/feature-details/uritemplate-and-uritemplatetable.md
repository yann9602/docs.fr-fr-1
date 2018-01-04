---
title: UriTemplate et UriTemplateTable
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5cbbe03f-4a9e-4d44-9e02-c5773239cf52
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ac77fe2c83828d2cc9473417d2b29b2d2e540923
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="uritemplate-and-uritemplatetable"></a>UriTemplate et UriTemplateTable
Les développeurs de sites Web ont besoin de pouvoir décrire la forme et la disposition des URI auxquels leurs services répondent. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a ajouté deux nouvelles classes pour permettre aux développeurs de mieux contrôler leurs URI. <xref:System.UriTemplate> et <xref:System.UriTemplateTable> forment la base du moteur de répartition reposant sur les URI dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Ces classes peuvent également être utilisées seules, ce qui permet aux développeurs de tirer parti des modèles et du mécanisme du mappage des URI sans avoir à implémenter un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="templates"></a>Modèles  
 Un modèle est un moyen de décrire un ensemble d'URI relatifs. L'ensemble de modèles URI présentés dans le tableau suivant montre comment peut être défini un système qui récupère différents types d'informations météorologiques.  
  
|Données|Modèle|  
|----------|--------------|  
|Prévision par pays|météo/pays|  
|Prévision par état|météo/{état}|  
|Prévision par ville|météo/{état}/{ville}|  
|Prévision par activité|météo/{état}/{ville}/{activité}|  
  
 Cette table décrit un ensemble d'URI structurellement semblables. Chaque entrée est un modèle URI. Les segments entre accolades décrivent des variables. Les segments hors accolades décrivent des chaînes littérales. Les classes de modèle [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] permettent à un développeur de prendre un URI entrant, par exemple "/météo/wa/seattle/vélo", et de le faire correspondre à un modèle qui le décrit, "/météo/{état}/{ville}/{activité}".  
  
## <a name="uritemplate"></a>UriTemplate  
 <xref:System.UriTemplate> est une classe qui encapsule un modèle URI. Le constructeur prend un paramètre de chaîne qui définit le modèle. Cette chaîne contient le modèle au format décrit dans la section suivante. La classe <xref:System.UriTemplate> fournit des méthodes qui vous permettent de faire correspondre un URI entrant à un modèle, de générer un URI a partir d'un modèle, de récupérer une collection de noms de variables utilisés dans le modèle, de déterminer si deux modèles sont équivalents et de retourner la chaîne du modèle.  
  
 <xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> prend une adresse de base et un URI candidat et tente de faire correspondre l'URI au modèle. Si la correspondance est réussie, une instance <xref:System.UriTemplateMatch> est retournée. L'objet <xref:System.UriTemplateMatch> contient un URI de base, l'URI candidat, une collection nom/valeur des paramètres de la requête, un tableau des segments du chemin d'accès relatif, une collection nom/valeur des variables mises en correspondance, l'instance <xref:System.UriTemplate> utilisée pour exécuter la correspondance, une chaîne contenant toute partie non appariée de l'URI candidat (utilisé lorsque le modèle comprend un caractère générique) et un objet associé au modèle.  
  
> [!NOTE]
>  La classe <xref:System.UriTemplate> ignore le schéma et le numéro de port lors de la mise en correspondance d'un URI candidat à un modèle.  
  
 Deux méthodes vous permettent de générer un URI à partir d'un modèle, <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> et <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>. <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> prend une adresse de base et une collection nom/valeur de paramètres. Ces paramètres sont substitués aux variables lorsque le modèle est lié. <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> prend les paires nom/valeur et les substitue de gauche à droite.  
  
 <xref:System.UriTemplate.ToString> retourne la chaîne du modèle.  
  
 La propriété <xref:System.UriTemplate.PathSegmentVariableNames%2A> contient une collection des noms des variables utilisés dans les segments de chemin d'accès de la chaîne du modèle.  
  
 <xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> prend <xref:System.UriTemplate> comme paramètre et retourne une valeur booléenne qui spécifie si les deux modèles sont équivalents. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] la section intitulée Équivalence des modèles, un peu plus loin dans cette rubrique.  
  
 <xref:System.UriTemplate> est conçu pour utiliser tout schéma URI conforme à la grammaire d'URI HTTP. Les éléments suivants illustrent des modèles URI pris en charge.  
  
-   http://  
  
-   https://  
  
-   net.tcp://  
  
-   net.pipe://  
  
-   sb://  
  
 Des schémas tels que file:// et urn:// ne sont pas conformes à la grammaire d'URI HTTP et entraînent des résultats imprévisibles en cas d'utilisation avec les modèles URI.  
  
### <a name="template-string-syntax"></a>Syntaxe de la chaîne du modèle  
 Un modèle se compose de trois parties : un chemin d'accès, une requête facultative et un fragment facultatif. Pour obtenir un exemple, consultez le modèle suivant :  
  
```  
"/weather/{state}/{city}?forecast={length)#frag1  
```  
  
 Le chemin d’accès est "/météo/{état}/{ville}", la demande est "?prévision={durée}, et le fragment est "#frag1".  
  
 Les barres obliques de début et de fin sont facultatives dans l'expression du chemin d'accès. Les expressions de la requête et du fragment peuvent toutes deux être complètement omises. Un chemin d’accès se compose d’une série de segments délimités par '/', chaque segment peut avoir une valeur littérale, un nom de variable (écrit entre {accolades}) ou un caractère générique (écrit comme\*'). Dans le modèle précédent, le segment "\météo\" est une valeur littérale tandis que "{état}" et "{ville}" sont des variables. Variables tirent leur nom à partir du contenu de leurs accolades et elles peuvent être remplacées ultérieurement par une valeur concrète pour créer un *URI fermé*. Le caractère générique est facultatif, mais il ne peut apparaître qu’à la fin de l’URI, où il correspond logiquement à « la suite du chemin d’accès ».  
  
 L'expression de la demande, le cas échant, spécifie une série de paires nom/valeur non ordonnées délimitées par '&'. Les éléments de l'expression de la demande peuvent être des paires littérales (x=2) ou une paire variable (x = {var}). Seule la partie droite de la requête peut comporter une expression variable. ({Nom} = {Valeur} n'est pas autorisé. Les valeurs non couplées (?x) ne sont pas autorisées. Il n'y a aucune différence entre une expression de demande vide et une expression de demande qui consiste en un '?' unique (les deux signifiant « aucune demande »).  
  
 L'expression du fragment peut se composer d'une valeur littérale ; aucune variable n'est autorisée.  
  
 Tous les noms de variables du modèle dans une chaîne de modèle doivent être uniques. Les noms des variables du modèle ne respectent pas la casse.  
  
 Exemples de chaînes de modèle valides :  
  
-   ""  
  
-   "/chaussure"  
  
-   "/chaussure/*"  
  
-   "{chaussure}/bateau"  
  
-   « {CHAUSSURE} / {bateau} /bed/ {quilt} »  
  
-   « CHAUSSURE / {bateau} »  
  
-   « CHAUSSURE / {bateau} / * »  
  
-   « CHAUSSURE/bateau ? x = 2 »  
  
-   « CHAUSSURE / {bateau} ? x = {lit} »  
  
-   "chaussure/{bateau}?x={lit}&y=bande"  
  
-   « ? x = {CHAUSSURE} »  
  
-   "chaussure?x=3&y={var}  
  
 Exemples de chaînes de modèle non valides :  
  
-   « {CHAUSSURE} / {CHAUSSURE} / x = 2 » – noms de variable en double.  
  
-   « {CHAUSSURE} /bateau/ ? lit = {CHAUSSURE} » : les noms de variable en double.  
  
-   « ? x = 2 & x = 3 » – les paires nom/valeur dans une chaîne de requête doivent être uniques, même si elles sont des littéraux.  
  
-   « ? x = 2 & » – chaîne de requête est incorrecte.  
  
-   « ? 2 & x = {CHAUSSURE} » – la chaîne de requête doit être des paires nom/valeur.  
  
-   « ? y = 2 & & X = 3 » – chaîne de requête doit être des paires nom-valeur, les noms ne peut pas commencer par '&'.  
  
### <a name="compound-path-segments"></a>Segments de chemin d’accès composés  
 Les segments de chemin d’accès composés permettent à un segment du chemin d’accès de l’URI unique de contenir plusieurs variables ainsi que des variables associées à des littéraux. Les éléments suivants illustrent des segments de chemin d’accès composés valides.  
  
-   /nom_de_fichier.{ext}/  
  
-   /{nom_de_fichier}.jpg/  
  
-   /{nom_de_fichier}.{ext}/  
  
-   /{a}.{b}someLiteral{c}({d})/  
  
 Les exemples suivants illustrent des segments de chemin d'accès non valides.  
  
-   /{} - Les variables doivent être nommées.  
  
-   /{chaussure}{bateau} – Les variables doivent être séparées par un littéral.  
  
### <a name="matching-and-compound-path-segments"></a>Segments de chemin d'accès composés et correspondants  
 Les segments de chemin d’accès composés vous permettent de définit un modèle d’URI ayant plusieurs variables dans un seul segment de chemin d’accès. Par exemple, dans la chaîne de modèle suivant : « adresses / {état}. {Ville} » deux variables (état et ville) sont définis dans le même segment. Ce modèle correspondrait à une URL comme « http://example.com/Washington.Redmond », mais il correspond également à une URL comme « http://example.com/Washington.Redmond.Microsoft ». Dans ce cas, la variable d’état contiendra « Washington » et la variable ville contiendra « Redmond.Microsoft ». Dans ce cas, tout texte (sauf ‘/’) correspondra à la variable {ville}. Si vous souhaitez un modèle qui ne corresponde pas le texte « supplémentaire », placez la variable dans un segment de modèle séparé, par exemple : « adresses / {état} / {ville}.  
  
### <a name="named-wildcard-segments"></a>Segments de caractère générique nommés  
 Un segment de caractère générique nommé est tout segment variable de chemin d’accès dont le nom de variable commence par le caractère générique ’*’. La chaîne de modèle suivante contient un segment de caractère générique nommé « chaussure ».  
  
```  
"literal/{*shoe}"  
```  
  
 Les segments de caractère générique doivent respecter les règles suivantes :  
  
-   Il peut y avoir tout au plus un segment de caractère générique nommé pour chaque chaîne de modèle.  
  
-   Un segment de caractère générique nommé doit apparaître à l'extrémité droite du chemin d'accès.  
  
-   Un segment de caractère générique nommé ne peut pas coexister avec un segment de caractère générique anonyme dans la même chaîne de modèle.  
  
-   Le nom d'un segment de caractère générique nommé doit être unique.  
  
-   Les segments de caractère générique nommés ne peuvent pas comporter de valeurs par défaut.  
  
-   Les segments de caractère générique nommé ne peut pas se terminer par « / ».  
  
### <a name="default-variable-values"></a>Valeurs de variables par défaut  
 Les valeurs de variables par défaut vous permettent de spécifier les valeurs par défaut des variables dans un modèle. Les variables par défaut peuvent être spécifiées entre des accolades qui les déclarent ou comme une collection passée au constructeur UriTemplate. Le modèle suivant démontre deux méthodes pour spécifier un <xref:System.UriTemplate> comportant des variables avec des valeurs par défaut.  
  
```  
UriTemplate t = new UriTemplate("/test/{a=1}/{b=5}");  
```  
  
 Ce modèle déclare une variable nommée `a` dont la valeur par défaut est `1` et une variable nommée `b` dont la valeur par défaut est `5`.  
  
> [!NOTE]
>  Seules les variables de segment de chemin d'accès peuvent avoir des valeurs par défaut. Les variables de chaîne de requête, les variables de segments composés et les variables de caractère générique nommées ne peuvent pas avoir des valeurs par défaut.  
  
 Le code suivant montre comment les valeurs de variables par défaut sont gérées lors de la mise en correspondance d'un URI candidat.  
  
```  
Uri baseAddress = new Uri("http://localhost:800   
Dictionary<string,string> defVals = new Dictionary<string,string> {{"a","1"}, {"b", "5"}};  
UriTemplate t = new UriTemplate("/test/{a}/{b}", defVals);0");  
UriTemplate t = new UriTemplate("/{state=WA}/{city=Redmond}/", true);  
Uri candidate = new Uri("http://localhost:8000/OR");  
  
UriTemplateMatch m1 = t.Match(baseAddress, candidate);  
  
// Display contents of BoundVariables  
foreach (string key in m1.BoundVariables.AllKeys)  
{  
    Console.WriteLine("\t\t{0}={1}", key, m1.BoundVariables[key]);  
}  
// The output of the above code is  
// Template: /{state=WA}/{city=Redmond}/  
// Candidate URI: http://localhost:8000/OR  
// BoundVariables:  
//      STATE=OR  
//       CITY=Redmond  
```  
  
> [!NOTE]
>  Un URI tel que http://localhost:8000/// ne correspond pas au modèle indiqué dans le code précédent ; en revanche, un URI tel que http://localhost:8000/ lui correspond.  
  
 Le code suivant montre comment les valeurs de variables par défaut sont gérées à la création d'un URI avec un modèle.  
  
```  
Uri baseAddress = new Uri("http://localhost:8000/");  
Dictionary<string,string> defVals = new Dictionary<string,string> {{"a","1"}, {"b", "5"}};  
UriTemplate t = new UriTemplate("/test/{a}/{b}", defVals);  
NameValueCollection vals = new NameValueCollection();  
vals.Add("a", "10");  
  
Uri boundUri = t.BindByName(baseAddress, vals);  
Console.WriteLine("BaseAddress: {0}", baseAddress);  
Console.WriteLine("Template: {0}", t.ToString());  
  
Console.WriteLine("Values: ");  
foreach (string key in vals.AllKeys)  
{  
    Console.WriteLine("\tKey = {0}, Value = {1}", key, vals[key]);  
}  
Console.WriteLine("Bound URI: {0}", boundUri);  
  
// The output of the preceding code is  
// BaseAddress: http://localhost:8000/  
// Template: /test/{a}/{b}  
// Values:  
//     Key = a, Value = 10  
// Bound URI: http://localhost:8000/test/10/5  
```  
  
 Si une variable a une valeur par défaut `null`, quelques contraintes supplémentaires s'appliquent. Une variable peut avoir une valeur par défaut `null` si elle est contenue dans le segment qui se trouve à l'extrémité droite de la chaîne de modèle ou si tous les segments à droite du segment ont des valeurs par défaut `null`. Les exemples suivants illustrent des chaînes de modèle comportant des valeurs par défaut `null` valides :  
  
-   ```  
    UriTemplate t = new UriTemplate("shoe/{boat=null}");  
    ```  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=null}/{boat=null}");  
    ```  
  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=1}/{boat=null}");  
    ```  
 Les exemples suivants illustrent des chaînes de modèle comportant des valeurs par défaut `null` non valides :  
  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=null}/boat"); // null default must be in the right most path segment  
    ```  
  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=null}/{boat=x}/{bed=null}"); // shoe cannot have a null default because boat does not have a default null value  
    ```  
### <a name="default-values-and-matching"></a>Valeurs par défaut et correspondance  
 Lorsque vous mettez en correspondance un URI candidat avec un modèle comportant des valeurs par défaut, si des valeurs ne sont pas spécifiées dans l'URI candidat, les valeurs par défaut seront placées dans la collection <xref:System.UriTemplateMatch.BoundVariables%2A>.  
  
### <a name="template-equivalence"></a>Équivalence des modèles  
 Deux modèles sont dits *structurellement équivalents* lorsque tous leurs littéraux correspondent et ils ont des variables dans les mêmes segments. Par exemple, les deux modèles suivants sont structurellement équivalents :  
  
-   /a/{var1}/b b/{var2}?x=1&y=2  
  
-   a/{x}/b%20b/{var1}?y=2&x=1  
  
-   a/{y}/B%20B/{z}/?y=2&x=1  
  
 Quelques points à noter :  
  
-   Si un modèle contient des barres obliques de début, seule la première est ignorée.  
  
-   Lors de la comparaison des chaînes de modèles pour rechercher une équivalence structurelle, la casse est ignorée pour les noms de variables et les segments de chemin d’accès, mais les chaînes de demande respectent la casse.  
  
-   Les chaînes de demande ne sont pas ordonnées.  
  
## <a name="uritemplatetable"></a>UriTemplateTable  
 La classe <xref:System.UriTemplateTable> représente une table associative d'objets <xref:System.UriTemplate> liés à un objet choisi par le développeur. Une <xref:System.UriTemplateTable> doit contenir au moins un <xref:System.UriTemplate> avant d'appeler <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>. Le contenu d'une  <xref:System.UriTemplateTable> peut être modifié jusqu'à l'appel de <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>. La validation est exécutée lorsque <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> est appelée. Le type de validation exécuté dépend de la valeur du paramètre `allowMultiple` de <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.  
  
 Lorsque <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> est appelée en passant `false`, la <xref:System.UriTemplateTable> vérifie qu'il n'y a pas de modèle dans la table. Si elle recherche des modèles structurellement équivalents, elle lève une exception. À utiliser conjointement avec <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> lorsque vous souhaitez garantir qu'un seul modèle correspond à un URI entrant.  
  
 Si <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> est appelée en passant dans `true`, <xref:System.UriTemplateTable> autorise la présence de plusieurs modèles structurellement équivalents dans une <xref:System.UriTemplateTable>.  
  
 Si un ensemble d'objets <xref:System.UriTemplate> ajoutés à une <xref:System.UriTemplateTable> contiennent des chaînes de demande, ils ne doivent pas être ambigus. Les chaînes de demande identiques sont autorisées.  
  
> [!NOTE]
>  Alors que la <xref:System.UriTemplateTable> accepte les adresses de base utilisant des schémas autres que HTTP, le schéma et le numéro de port sont ignorés lors de la mise en correspondance des URI candidats avec les modèles.  
  
### <a name="query-string-ambiguity"></a>Ambiguïté des chaînes de demande  
 Les modèles qui partagent un chemin d'accès équivalent contiennent des chaînes de demande ambiguës si un URI correspond à plusieurs modèles.  
  
 Les ensembles suivants de chaînes de requête ne sont pas ambigus entre eux :  
  
-   ?x=1  
  
-   ?x=2  
  
-   ?x=3  
  
-   ?x=1&y={var}  
  
-   ?x=2&z={var}  
  
-   ?x=3  
  
-   ?x=1  
  
-   ?  
  
-   ? x={var}  
  
-   ?  
  
-   ?m=get&c=rss  
  
-   ?m=put&c=rss  
  
-   ?m=get&c=atom  
  
-   ?m=put&c=atom  
  
 Les ensembles suivants de modèles de chaînes de requête sont ambigus entre eux :  
  
-   ?x=1  
  
-   ?x={var}  
  
 "x=1" - correspond aux deux modèles.  
  
-   ?x=1  
  
-   ?y=2  
  
 "x=1&y=2" correspond aux deux modèles. C'est parce qu'une chaîne de demande peut contenir plus de variables de chaîne de demande que le modèle auquel elle correspond.  
  
-   ?x=1  
  
-   ?x=1&y={var}  
  
 "x=1&y=3" correspond aux deux modèles.  
  
-   ?x=3&y=4  
  
-   ?x=3&z=5  
  
> [!NOTE]
>  Les caractères á et Á sont considérés comme des caractères différents lorsqu'ils apparaissent dans le cadre d'un chemin d'accès d'URI ou d'un littéral de segment de chemin d'accès <xref:System.UriTemplate> (en revanche, les caractères a et A sont considérés comme identiques). Les caractères á et Á sont considérés comme identiques lorsqu'ils apparaissent dans le cadre d'un {nomVariable} <xref:System.UriTemplate> ou d'une chaîne de demande (a et A sont également considérés comme identiques).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du modèle de programmation HTTP web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)  
 [Modèle objet de programmation HTTP web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)  
 [UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-sample.md)  
 [Table UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)  
 [Répartiteur de table UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
