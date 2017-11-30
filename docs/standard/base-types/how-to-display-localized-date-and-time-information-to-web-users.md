---
title: "Comment : afficher des informations de date et d'heure localisées pour les utilisateurs du Web"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- formatting [.NET Framework], dates
- parsing strings [.NET Framework], date and time strings
- localization [.NET Framework], date and time displays
- formatting [.NET Framework], localized data
- displaying date and time data
- localized date displays [.NET Framework]
ms.assetid: 377fe93c-32be-421a-a30a-be639a46ede8
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 21493e0e0c9e42cf5efc42d86c8f126fbae9b392
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-localized-date-and-time-information-to-web-users"></a>Comment : afficher des informations de date et d'heure localisées pour les utilisateurs du Web
Comme une page Web peut être affichée n’importe où dans le monde, les opérations qui analysent et mettre en forme les valeurs de date et d’heure ne doivent pas compter sur un format par défaut (en général est le format de la culture locale du serveur de Web) lors de l’interaction avec l’utilisateur. Au lieu de cela, les formulaires Web qui gèrent les date et heure d’entrée de chaînes par l’utilisateur doivent analyser les chaînes à l’aide de la culture par défaut. De même, les données de date et d’heure doivent être affichées à l’utilisateur dans un format conforme à la culture de l’utilisateur. Cette rubrique montre comment procéder.  
  
### <a name="to-parse-date-and-time-strings-input-by-the-user"></a>Analyse de date et heure des chaînes d’entrée par l’utilisateur  
  
1.  Déterminez si le tableau de chaînes retourné par la <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> propriété est remplie. Si elle n’est pas le cas, passez à l’étape 6.  
  
2.  Si le tableau de chaînes retourné par la <xref:System.Web.HttpRequest.UserLanguages%2A> propriété est remplie, récupérez son premier élément. Le premier élément indique l’utilisateur par défaut ou langue et région.  
  
3.  Instancier une <xref:System.Globalization.CultureInfo> objet qui représente l’utilisateur de culture par défaut en appelant le <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> constructeur.  
  
4.  Appelez le `TryParse` ou `Parse` méthode de la <xref:System.DateTime> ou <xref:System.DateTimeOffset> type pour essayer la conversion. Utilisez une surcharge de la `TryParse` ou `Parse` méthode avec un `provider` paramètre et lui passer une des opérations suivantes :  
  
    -   Le <xref:System.Globalization.CultureInfo> objet créé à l’étape 3.  
  
    -   Le <xref:System.Globalization.DateTimeFormatInfo> objet qui est retourné par la <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> propriété de la <xref:System.Globalization.CultureInfo> objet créé à l’étape 3.  
  
5.  Si la conversion échoue, répétez les étapes 2 à 4 pour chaque élément restant dans le tableau de chaînes retournés par la <xref:System.Web.HttpRequest.UserLanguages%2A> propriété.  
  
6.  Si la conversion échoue encore ou si le tableau de chaînes retourné par la <xref:System.Web.HttpRequest.UserLanguages%2A> propriété est vide, d’analyser la chaîne à l’aide de la culture dite indifférente, qui est retourné par la <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> propriété.  
  
### <a name="to-parse-the-local-date-and-time-of-the-users-request"></a>Analyse de la date et heure locales de la demande de l’utilisateur  
  
1.  Ajouter un <xref:System.Web.UI.WebControls.HiddenField> à un formulaire Web.  
  
2.  Créez une fonction JavaScript qui gère la `onClick` événement d’un `Submit` bouton en écrivant la date et l’heure et décalage du fuseau horaire local à partir du temps universel coordonné (UTC) pour le <xref:System.Web.UI.WebControls.HiddenField.Value%2A> propriété. Utilisez un séparateur (par exemple, un point-virgule) pour séparer les deux composants de la chaîne.  
  
3.  Utilisez l’écran de Web <xref:System.Web.UI.Control.PreRender> flux de sortie d’événements pour injecter la fonction dans le code HTML en passant le texte du script à la <xref:System.Web.UI.ClientScriptManager.RegisterClientScriptBlock%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=nameWithType> (méthode).  
  
4.  Connecter le Gestionnaire d’événements pour le `Submit` du bouton `onClick` événement en fournissant le nom de la fonction JavaScript à la `OnClientClick` attribut de la `Submit` bouton.  
  
5.  Créer un gestionnaire pour le `Submit` du bouton <xref:System.Web.UI.WebControls.Button.Click> événement.  
  
6.  Dans le Gestionnaire d’événements, déterminez si le tableau de chaînes retourné par la <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> propriété est remplie. Si elle n’est pas le cas, passez à l’étape 14.  
  
7.  Si le tableau de chaînes retourné par la <xref:System.Web.HttpRequest.UserLanguages%2A> propriété est remplie, récupérez son premier élément. Le premier élément indique l’utilisateur par défaut ou langue et région.  
  
8.  Instancier une <xref:System.Globalization.CultureInfo> objet qui représente l’utilisateur de culture par défaut en appelant le <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> constructeur.  
  
9. Passez la chaîne assignée à la <xref:System.Web.UI.WebControls.HiddenField.Value%2A> propriété le <xref:System.String.Split%2A> méthode pour stocker la représentation sous forme de chaîne d’heure et date locales de l’utilisateur et la représentation sous forme de chaîne du décalage de fuseau horaire local de l’utilisateur dans les éléments de tableau séparés.  
  
10. Appelez le <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> ou <xref:System.DateTime.TryParse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%2CSystem.DateTime%40%29?displayProperty=nameWithType> méthode pour convertir la date et l’heure de demande de l’utilisateur à un <xref:System.DateTime> valeur. Utilisez une surcharge de la méthode avec un `provider` paramètre et lui passer une des opérations suivantes :  
  
    -   Le <xref:System.Globalization.CultureInfo> objet créé à l’étape 8.  
  
    -   Le <xref:System.Globalization.DateTimeFormatInfo> objet qui est retourné par la <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> propriété de la <xref:System.Globalization.CultureInfo> objet créé à l’étape 8.  
  
11. Si l’opération d’analyse à l’étape 10 échoue, passez à l’étape 13. Sinon, appelez le <xref:System.UInt32.Parse%28System.String%29?displayProperty=nameWithType> méthode pour convertir la représentation sous forme de chaîne du décalage de fuseau horaire de l’utilisateur en un entier.  
  
12. Instancier une <xref:System.DateTimeOffset> qui représente l’heure locale de l’utilisateur en appelant le <xref:System.DateTimeOffset.%23ctor%28System.DateTime%2CSystem.TimeSpan%29?displayProperty=nameWithType> constructeur.  
  
13. Si la conversion à l’étape 10 échoue, répétez les étapes 7 à 12 pour chaque élément restant dans le tableau de chaînes retournés par la <xref:System.Web.HttpRequest.UserLanguages%2A> propriété.  
  
14. Si la conversion échoue encore ou si le tableau de chaînes retourné par la <xref:System.Web.HttpRequest.UserLanguages%2A> propriété est vide, d’analyser la chaîne à l’aide de la culture dite indifférente, qui est retourné par la <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> propriété. Répétez les étapes 7 à 12.  
  
 Le résultat est un <xref:System.DateTimeOffset> objet qui représente l’heure locale de l’utilisateur de votre page Web. Vous pouvez ensuite déterminer l’heure UTC équivalente en appelant le <xref:System.DateTimeOffset.ToUniversalTime%2A> (méthode). Vous pouvez également déterminer la date et heure équivalentes sur votre serveur Web en appelant le <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> (méthode) et le passage d’une valeur <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> en tant que le fuseau horaire pour convertir l’heure à.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant contient la source HTML et le code d’un formulaire Web ASP.NET qui invite l’utilisateur à entrer une valeur de date et d’heure. Un script côté client écrit également des informations sur la date locales et l’heure de demande de l’utilisateur et le décalage de fuseau horaire de l’utilisateur à l’heure UTC dans un champ masqué. Cette information est ensuite analysée par le serveur, qui retourne une page Web qui affiche l’entrée d’utilisateur. Il affiche également la date et l’heure de demande de l’utilisateur à l’aide d’heure locale de l’utilisateur, l’heure sur le serveur et l’heure UTC.  
  
 [!code-aspx-csharp[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/cs/GetDateInfo.aspx#1)]
 [!code-aspx-vb[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/vb/GetDateInfo.aspx#1)]
  
 Le script côté client appelle le code JavaScript `toLocaleString` (méthode). Cela génère une chaîne qui suit les conventions de mise en forme de paramètres régionaux de l’utilisateur, ce qui est plus susceptible d’être analysée avec succès sur le serveur.  
  
 Le <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> propriété est remplie par les noms de culture qui figurent dans `Accept-Language` en-têtes inclus dans une requête HTTP. Toutefois, certains navigateurs n’incluent `Accept-Language` en-têtes dans leurs demandes et les utilisateurs peuvent également supprimer complètement les en-têtes. Il est donc important d’avoir une culture de secours lors de l’analyse de l’entrée d’utilisateur. En général, la culture de secours est la culture dite indifférente retournée par <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Les utilisateurs peuvent également fournir Internet Explorer avec des noms de cultures qu’ils entrent dans une zone de texte, il peut arriver que les noms de cultures n’est peut-être pas valides. Il est donc important d’utiliser la gestion des exceptions lorsque vous instanciez un <xref:System.Globalization.CultureInfo> objet.  
  
 Lorsque récupérées à partir d’une requête HTTP soumise par Internet Explorer, le <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> tableau est rempli par ordre de préférence de l’utilisateur. Le premier élément du tableau contient le nom de culture/région principale de l’utilisateur. Si le tableau contient des éléments supplémentaires, Internet Explorer leur assigne arbitrairement un spécificateur de qualité, qui est délimité par un point-virgule à partir du nom de culture. Par exemple, une entrée pour la culture fr-FR peut prendre la forme `fr-FR;q=0.7`.  
  
 L’exemple appelle la <xref:System.Globalization.CultureInfo.%23ctor%2A> constructeur avec son `useUserOverride` paramètre la valeur `false` pour créer un nouveau <xref:System.Globalization.CultureInfo> objet. Cela garantit que, si le nom de culture est le nom de culture par défaut sur le serveur, la nouvelle <xref:System.Globalization.CultureInfo> objet créé par le constructeur de classe contient les paramètres par défaut d’une culture et ne reflète pas les paramètres de substitution à l’aide du serveur  **Régional et Options de langue** application. Les valeurs des paramètres substitués sur le serveur sont peu susceptibles d’exister sur le système de l’utilisateur ou qu’elles apparaissent dans l’entrée d’utilisateur.  
  
 Étant donné que cet exemple analyse deux représentations sous forme de chaîne d’une date et d’heure (une seule entrée par l’utilisateur, l’autre est stockée dans le champ masqué), il définit les <xref:System.Globalization.CultureInfo> les objets qui peuvent être nécessaires à l’avance. Il crée un tableau de <xref:System.Globalization.CultureInfo> objets est supérieur au nombre d’éléments retournés par la <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> propriété. Il instancie ensuite un <xref:System.Globalization.CultureInfo> de l’objet pour chaque chaîne de langue/région, ainsi qu’un <xref:System.Globalization.CultureInfo> objet qui représente <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.  
  
 Votre code peut appeler le <xref:System.DateTime.Parse%2A> ou <xref:System.DateTime.TryParse%2A> méthode pour convertir la représentation sous forme de chaîne de l’utilisateur d’une date et l’heure à un <xref:System.DateTime> valeur. Les appels répétés à une méthode d’analyse peuvent être nécessaire pour une opération d’analyse unique. Par conséquent, le <xref:System.DateTime.TryParse%2A> méthode est préférable car elle retourne `false` si une opération d’analyse échoue. En revanche, la gestion des exceptions répétées pouvant être levées par le <xref:System.DateTime.Parse%2A> méthode peut être très coûteux dans une application Web.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Pour compiler le code, créez un [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] page Web sans code-behind. Copiez ensuite l’exemple dans la page Web pour qu’il remplace tout le code existant. Le [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] page Web doit contenir les contrôles suivants :  
  
-   A <xref:System.Web.UI.WebControls.Label> contrôle, qui n’est pas référencé dans le code. Définir son <xref:System.Web.UI.WebControls.TextBox.Text%2A> propriété « Entrez un nombre : ».  
  
-   un contrôle <xref:System.Web.UI.WebControls.TextBox> nommé `DateString` ;  
  
-   un contrôle <xref:System.Web.UI.WebControls.Button> nommé `OKButton` ; Définir son <xref:System.Web.UI.WebControls.Button.Text%2A> propriété sur « OK ».  
  
-   un contrôle <xref:System.Web.UI.WebControls.HiddenField> nommé `DateInfo` ;  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Pour empêcher un utilisateur d’injection de script dans le flux de données HTML, l’entrée d’utilisateur doit jamais être répétée directement dans la réponse du serveur. Au lieu de cela, il doit être encodé à l’aide de la <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType> (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution d’opérations de mise en forme](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [Standard Date and Time Format Strings](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)  
 [Custom Date and Time Format Strings](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)  
 [Analyse de chaînes de date et d’heure](../../../docs/standard/base-types/parsing-datetime.md)
