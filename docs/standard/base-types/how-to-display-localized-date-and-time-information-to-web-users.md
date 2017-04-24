---
title: "Comment&#160;: afficher des informations de date et d&#39;heure localis&#233;es pour les utilisateurs du Web | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "afficher les données de date et d'heure"
  - "mise en forme (.NET Framework), dates"
  - "mise en forme (.NET Framework), données localisées"
  - "localisation (.NET Framework), affichages de la date et l'heure"
  - "affichages de date localisée (.NET Framework)"
  - "analyser des chaînes (.NET Framework), chaînes date et heure"
ms.assetid: 377fe93c-32be-421a-a30a-be639a46ede8
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: afficher des informations de date et d&#39;heure localis&#233;es pour les utilisateurs du Web
Comme une page Web peut être affichée n'importe où dans le monde, les opérations d'analyse et de mise en forme des valeurs de date et d'heure ne doivent pas dépendre d'un format par défaut \(généralement le format de la culture locale du serveur Web\) lors de l'interaction avec l'utilisateur.  Les formulaires Web qui gèrent les chaînes de date et d'heure entrées par l'utilisateur doivent analyser les chaînes à l'aide de la culture par défaut de ce dernier.  De même, les données de date et d'heure doivent être affichées dans un format conforme à la culture de l'utilisateur.  Cette rubrique indique comment faire.  
  
### Pour analyser les chaînes de date et d'heure entrées par l'utilisateur  
  
1.  Déterminez si le tableau de chaînes retourné par la propriété <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=fullName> est rempli.  Si ce n'est pas le cas, passez à l'étape 6.  
  
2.  Si le tableau de chaînes retourné par la propriété <xref:System.Web.HttpRequest.UserLanguages%2A> est rempli, récupérez son premier élément.  Le premier élément indique la langue et la région par défaut ou préférées de l'utilisateur.  
  
3.  Instanciez un objet <xref:System.Globalization.CultureInfo> qui représente la culture par défaut de l'utilisateur en appelant le constructeur <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=fullName>.  
  
4.  Appelez la méthode `TryParse` ou `Parse` du type <xref:System.DateTime> ou <xref:System.DateTimeOffset> pour essayer de procéder à la conversion.  Utilisez une surcharge de la méthode `TryParse` ou `Parse` avec un paramètre `provider` et passez\-lui l'un ou l'autre des éléments suivants :  
  
    -   l'objet <xref:System.Globalization.CultureInfo> créé à l'étape 3 ;  
  
    -   l'objet <xref:System.Globalization.DateTimeFormatInfo> retourné par la propriété <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> de l'objet <xref:System.Globalization.CultureInfo> créé à l'étape 3.  
  
5.  Si la conversion échoue, répétez les étapes 2 à 4 pour chaque élément restant du tableau de chaînes retourné par la propriété <xref:System.Web.HttpRequest.UserLanguages%2A>.  
  
6.  Si la conversion échoue encore ou si le tableau de chaînes retourné par la propriété <xref:System.Web.HttpRequest.UserLanguages%2A> est vide, analysez la chaîne en utilisant la culture indifférente retournée par la propriété <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.  
  
### Pour analyser les date et heure locales de la demande de l'utilisateur  
  
1.  Ajoutez un contrôle <xref:System.Web.UI.WebControls.HiddenField> à un formulaire Web.  
  
2.  Créez une fonction JavaScript qui gère l'événement `onClick` d'un bouton `Submit` en écrivant la date et l'heure actuelles ainsi que le décalage par rapport au temps universel coordonné \(offset UTC\) dans la propriété <xref:System.Web.UI.WebControls.HiddenField.Value%2A>.  Utilisez un séparateur \(tel qu'un point\-virgule\) pour séparer les deux composants de la chaîne.  
  
3.  Utilisez l'événement <xref:System.Web.UI.Control.PreRender> du formulaire Web pour injecter la fonction dans le flux de sortie HTML en passant le texte du script à la méthode <xref:System.Web.UI.ClientScriptManager.RegisterClientScriptBlock%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=fullName>.  
  
4.  Connectez le gestionnaire d'événements à l'événement `onClick` du bouton `Submit` en fournissant le nom de la fonction JavaScript à l'attribut `OnClientClick` du bouton `Submit`.  
  
5.  Créez un gestionnaire pour l'événement <xref:System.Web.UI.WebControls.Button.Click> du bouton `Submit`.  
  
6.  Dans le gestionnaire d'événements, déterminez si le tableau de chaînes retourné par la propriété <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=fullName> est rempli.  Si ce n'est pas le cas, passez à l'étape 14.  
  
7.  Si le tableau de chaînes retourné par la propriété <xref:System.Web.HttpRequest.UserLanguages%2A> est rempli, récupérez son premier élément.  Le premier élément indique la langue et la région par défaut ou préférées de l'utilisateur.  
  
8.  Instanciez un objet <xref:System.Globalization.CultureInfo> qui représente la culture par défaut de l'utilisateur en appelant le constructeur <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=fullName>.  
  
9. Passez la chaîne assignée à la propriété <xref:System.Web.UI.WebControls.HiddenField.Value%2A> à la méthode <xref:System.String.Split%2A> pour stocker la représentation sous forme de chaîne des date et heure locales de l'utilisateur ainsi que la représentation sous forme de chaîne du décalage de fuseau horaire local de l'utilisateur dans des éléments de tableau séparés.  
  
10. Appelez la méthode <xref:System.DateTime.Parse%2A?displayProperty=fullName> ou <xref:System.DateTime.TryParse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%2CSystem.DateTime%40%29?displayProperty=fullName> pour convertir les date et heure de la demande de l'utilisateur en une valeur <xref:System.DateTime>.  Utilisez une surcharge de la méthode avec un paramètre `provider` et passez\-lui l'un ou l'autre des éléments suivants :  
  
    -   l'objet <xref:System.Globalization.CultureInfo> créé à l'étape 8 ;  
  
    -   l'objet <xref:System.Globalization.DateTimeFormatInfo> retourné par la propriété <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> de l'objet <xref:System.Globalization.CultureInfo> créé à l'étape 8.  
  
11. Si l'opération d'analyse de l'étape 10 échoue, passez à l'étape 13.  Sinon, appelez la méthode <xref:System.UInt32.Parse%28System.String%29?displayProperty=fullName> pour convertir la représentation sous forme de chaîne du décalage de fuseau horaire de l'utilisateur en un entier.  
  
12. Instanciez un objet <xref:System.DateTimeOffset> qui représente l'heure locale de l'utilisateur en appelant le constructeur <xref:System.DateTimeOffset.%23ctor%28System.DateTime%2CSystem.TimeSpan%29?displayProperty=fullName>.  
  
13. Si la conversion de l'étape 10 échoue, répétez les étapes 7 à 12 pour chaque élément restant du tableau de chaînes retourné par la propriété <xref:System.Web.HttpRequest.UserLanguages%2A>.  
  
14. Si la conversion échoue encore ou si le tableau de chaînes retourné par la propriété <xref:System.Web.HttpRequest.UserLanguages%2A> est vide, analysez la chaîne en utilisant la culture indifférente retournée par la propriété <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.  Répétez ensuite les étapes 7 à 12.  
  
 Le résultat est un objet <xref:System.DateTimeOffset> qui représente l'heure locale de l'utilisateur de votre page Web.  Vous pouvez ensuite déterminer l'heure UTC équivalente en appelant la méthode <xref:System.DateTimeOffset.ToUniversalTime%2A>.  Vous pouvez également déterminer les date et heure équivalentes sur votre serveur Web en appelant la méthode <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=fullName> et en passant une valeur <xref:System.TimeZoneInfo.Local%2A?displayProperty=fullName> en tant que fuseau horaire vers lequel convertir l'heure.  
  
## Exemple  
 L'exemple suivant contient à la fois la source HTML et le code pour un formulaire Web ASP.NET qui demande à l'utilisateur d'entrer une valeur de date et d'heure.  Un script côté client écrit également des informations sur les date et heure locales de la demande de l'utilisateur et le décalage par rapport à l'heure UTC \(offset de fuseau horaire de l'utilisateur\) dans un champ masqué.  Ces informations sont ensuite analysées par le serveur qui retourne une page Web affichant l'entrée de l'utilisateur.  Les date et heure de la demande de l'utilisateur sont également affichées en utilisant l'heure locale de l'utilisateur, l'heure sur le serveur et l'heure UTC.  
  
 <!-- TODO: review snippet reference [!code-csharp[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/cs/GetDateInfo.aspx#1)]  -->
 <!-- TODO: review snippet reference [!code-vb[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/vb/GetDateInfo.aspx#1)]  -->  
  
 Le script côté client appelle la méthode `toLocaleString` JavaScript.  Une chaîne qui suit les conventions de mise en forme des paramètres régionaux de l'utilisateur est alors générée. Elle a plus de chances d'être analysée avec succès sur le serveur.  
  
 La propriété <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=fullName> est remplie à l'aide des noms de culture contenus dans les en\-têtes `Accept-Language` inclus dans une requête HTTP.  Toutefois, certains navigateurs n'incluent pas d'en\-têtes `Accept-Language` dans leurs demandes, et les utilisateurs peuvent également supprimer complètement les en\-têtes.  Il est donc important d'avoir une culture de secours lors de l'analyse de l'entrée d'utilisateur.  En général, la culture de secours est la culture indifférente retournée par <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.  Comme les utilisateurs peuvent également fournir à Internet Explorer des noms de culture qu'ils entrent dans une zone de texte, il peut arriver que ces noms ne soient pas valides.  Il est donc important d'utiliser la gestion des exceptions lors de l'instanciation d'un objet <xref:System.Globalization.CultureInfo>.  
  
 Lorsqu'il est récupéré d'une requête HTTP soumise par Internet Explorer, le tableau <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=fullName> est rempli par ordre de préférence de l'utilisateur.  Le premier élément du tableau comporte le nom de la culture\/région principale de l'utilisateur.  Si le tableau contient des éléments supplémentaires, Internet Explorer leur assigne arbitrairement un spécificateur de qualité séparé du nom de culture par un point\-virgule.  Par exemple, une entrée de la culture fr\-FR peut se présenter sous la forme `fr-FR;q=0.7`.  
  
 L'exemple appelle le constructeur <xref:System.Globalization.CultureInfo.%23ctor%2A> avec son paramètre `useUserOverride` défini à `false` pour créer un objet <xref:System.Globalization.CultureInfo>.  Ceci garantit que, si le nom de culture est celui utilisé par défaut sur le serveur, le nouvel objet <xref:System.Globalization.CultureInfo> créé par le constructeur de classe contient les paramètres par défaut d'une culture et ne reflète pas les paramètres substitués à l'aide de l'application **Options régionales et linguistiques** du serveur.  Il est peu probable que les valeurs des paramètres substitués sur le serveur existent sur le système de l'utilisateur ou qu'elles apparaissent dans l'entrée de l'utilisateur.  
  
 Comme cet exemple analyse deux représentations sous forme de chaîne des date et heure \(l'une est entrée par l'utilisateur, l'autre est stockée dans le champ masqué\), il définit les objets <xref:System.Globalization.CultureInfo> qui peuvent être requis à l'avance.  Il crée un tableau d'objets <xref:System.Globalization.CultureInfo> qui contient un élément de plus que ceux retournés par la propriété <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=fullName>.  Ensuite, il instancie un objet <xref:System.Globalization.CultureInfo> pour chaque chaîne de langue\/région, ainsi qu'un objet <xref:System.Globalization.CultureInfo> qui représente <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.  
  
 Votre code peut appeler la méthode <xref:System.DateTime.Parse%2A> ou <xref:System.DateTime.TryParse%2A> pour convertir la représentation sous forme de chaîne des date et heure de l'utilisateur en une valeur <xref:System.DateTime>.  Il se peut que vous deviez répéter les appels à une méthode d'analyse si vous effectuez une seule opération d'analyse.  Par conséquent, en cas d'échec d'une opération d'analyse, il est préférable d'utiliser la méthode <xref:System.DateTime.TryParse%2A>, car elle retourne la valeur `false`.  En revanche, la gestion des exceptions répétées pouvant être levées par la méthode <xref:System.DateTime.Parse%2A> risque d'être très onéreuse dans une application Web.  
  
## Compilation du code  
 Pour compiler le code, créez une page Web [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] sans code\-behind.  Copiez ensuite l'exemple dans la page Web pour qu'il remplace tout le code existant.  La page Web [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] doit contenir les contrôles suivants :  
  
-   un contrôle <xref:System.Web.UI.WebControls.Label> qui n'est pas référencé dans le code  \(affectez la valeur "Enter a Number:" à sa propriété <xref:System.Web.UI.WebControls.TextBox.Text%2A>\) ;  
  
-   un contrôle <xref:System.Web.UI.WebControls.TextBox> nommé `DateString` ;  
  
-   un contrôle <xref:System.Web.UI.WebControls.Button> nommé `OKButton` \(affectez la valeur "OK" à sa propriété <xref:System.Web.UI.WebControls.Button.Text%2A>\).  
  
-   un contrôle <xref:System.Web.UI.WebControls.HiddenField> nommé `DateInfo`.  
  
## Sécurité .NET Framework  
 Pour empêcher l'injection de script dans le flux de données HTML, l'entrée d'utilisateur ne doit jamais être répétée directement dans la réponse du serveur,  mais encodée à l'aide de la méthode <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=fullName>.  
  
## Voir aussi  
 [Exécution d'opérations de mise en forme](../../../docs/standard/base-types/performing-formatting-operations.md)   
 [Chaînes de format de date et d'heure standard](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)   
 [Chaînes de format de date et d'heure personnalisées](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)   
 [Analyse des chaînes de date et d'heure](../../../docs/standard/base-types/parsing-datetime.md)