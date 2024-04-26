<!DOCTYPE html>
<html lang="fr">
<body>
<div class="container">
         <section id="Projet-creation-dun-carnet-dordre" class="level1">
      <h1>Projet : Création d'un carnet d'ordre</h1>
      <hr>
      <section id="Analyse-et-Conception" class="level1">
      <h1 class="anchored" data-anchor-id="Analyse-et-Conception"> Analyse et Conception</h1>
      <section id="a.-Compréhension-Approfondie-des-Carnets-dOrdres" class="level3">
      <h3 class="anchored" data-anchor-id="a.--Compréhension-Approfondie-des-Carnets-dOrdres">a. Compréhension Approfondie des Carnets d'Ordres</h3>
      <p> Les carnets d'ordres doivent fonctionner de manière continue, reflétant un environnement dynamique où les participants peuvent à tout moment ajouter ou annuler des ordres. Cette flexibilité est essentielle pour simuler fidèlement le comportement des marchés financiers réels. Le projet que nous avons réalisé a pour but de créer un carnet d’ordres qui va être fonctionnel que cela soit pour stocker, exécuter, chercher ou même créer un ordre d’achat ou de vente. Il contient deux classes principales, la première est celle de la configuration qui va avoir pour objectif de créer un carnet d’ordre et de lui permettre de s’auto-gérer parfaitement. La seconde classe correspond à la création d’une interface qui va permettre à l’utilisateur de gérer directement le carnet d’ordre. Nous allons donc vous expliquer notre code étape par étape </p>
      <section id="b.-Mise-en-Avant-des-Concepts-de-Maker-et-Taker" class="level3">
      <h3 class="anchored" data-anchor-id="b.-Mise-en-Avant-des-Concepts-de-Maker-et-Taker">b. Mise en Avant des Concepts de Maker et Taker</h3>
      <p>- Maker : Les Makers ajoutent de la liquidité au marché en plaçant des ordres qui ne sont pas exécutés immédiatement, restant dans le carnet jusqu'à ce qu'un prix correspondant soit trouvé.</p>
      <p>- Taker : Les Takers retirent de la liquidité en exécutant des ordres contre les ordres existants dans le carnet, facilitant ainsi des transactions immédiates.</p>
      <p>Ces rôles influencent directement la dynamique de l'offre et de la demande et seront essentiels pour simuler le fonctionnement du marché.</p>
      <section id="c.-Intégration-des-Notions-de-Tick-et-Lot" class="level3">
      <h3 class="anchored" data-anchor-id="c.-Intégration-des-Notions-de-Tick-et-Lot">c. Intégration des Notions de Tick et Lot</h3>
      <p>- Tick : Le Tick représente le plus petit mouvement de prix possible pour un actif. Cette notion est cruciale pour déterminer comment les prix peuvent évoluer dans le carnet d'ordres.</p>
      <p>- Lot : Le Lot dénote la quantité minimale ou un multiple de cette quantité qu'un actif peut être échangé. Cette règle affecte la façon dont les ordres sont placés et exécutés.</p>
      <section id="Hypothèses-de-Construction-Révisées" class="level2">
          <h2 class="anchored" data-anchor-id="Hypothèses-de-Construction-Révisées">Hypothèses de Construction Révisées</h2>
          <p>1. Continuité et Flexibilité : Le simulateur gérera les ordres de manière continue, permettant à tout moment l'ajout et l'annulation d'ordres pour simuler un environnement de marché dynamique.</p>
          <p>2. Rôles Dynamiques de Maker et Taker : Le simulateur reconnaîtra et distinguera les actions des Makers et des Takers pour refléter leur impact sur la liquidité du marché.</p>
          <p>3. Respect des Contraintes de Tick et Lot : Les règles concernant les Ticks et les Lots sont intégrés à l'aide d'un bouton qui renvoie les valeurs à respecter pour l'utilisateur.</p>
      </section>
      <section id="Entités-Clés-et-Structure-de-Données" class="level2">
          <h2 class="anchored" data-anchor-id="Entités-Clés-et-Structure-de-Données">Entités Clés et Structure de Données</h2>
          <p>- Classe 'CarnetOrdre' : Représente un ordre dans le carnet avec des attributs pour le type d'ordre, la référence de l'actif, le prix et la quantité. </p>
          <p>- Classe 'CarnetOrdresGUI' : La classe CarnetOrdresGUI est une interface utilisateur pour visualiser et gérer un carnet d'ordres. </p>
      </section>
      <section id="Conclusion-et-Prochaine-Étape" class="level2">
          <h2 class="anchored" data-anchor-id="Conclusion-et-Prochaine-Étape">Conclusion et Prochaine Étape</h2>
          <p>La prochaine étape consistera à détailler le développement de la classe CarnetOrdres et à simuler son fonctionnement dans un environnement de marché.</p>
      </section>
      </section>
      
      <section id="Développement-de-la-Classe-CarnetOrdres" class="level1">
          <h1>Développement de la Classe CarnetOrdres</h1>
          <hr>
          <section id="Structure-de-la-Classe" class="level2">
              <h2 class="anchored" data-anchor-id="Structure-de-la-Classe">a. Structure de la Classe</h2>
              <p>La classe CarnetOrdres sera structurée pour gérer efficacement les ordres d'achat et de vente. Cette partie du code crée la classe CarnetOrdres, qui est le cœur de notre application de gestion des ordres. Lors de son initialisation, elle établit une connexion avec l'interface utilisateur (self.gui) pour permettre une interaction fluide entre la logique métier et l'interface graphique. Les variables self.ordres_achat et self.ordres_vente servent à stocker respectivement les ordres d'achat et de vente. Ces listes sont des conteneurs pour les données des ordres, telles que leur prix, leur quantité et leur identifiant. La liste self.transactions est destinée à enregistrer les transactions effectuées sur le marché. Chaque transaction est représentée sous forme de dictionnaire, capturant des détails tels que l'identifiant de l'ordre d'achat et de vente, ainsi que le prix et la quantité échangés. L'appel à self.lire_ordres(...) suggère l'existence d'une fonction pour charger les données initiales du carnet d'ordres à partir d'un fichier. Cela garantit que le carnet d'ordres est prérempli avec des données significatives au démarrage de l'application. Enfin, self.auto_executing est un indicateur booléen qui contrôle le mode continu de l'application. Lorsqu'il est activé, les ordres sont automatiquement exécutés à intervalles réguliers, offrant une fonctionnalité essentielle pour les traders qui souhaitent automatiser leurs transactions. </p>
              <pre><code class="language-python">class CarnetOrdres:
             import tkinter as tk
          from tkinter import ttk
          import tkinter.messagebox
          import random
          import time
          class CarnetOrdres:
              def __init__(self, gui):
                  self.gui = gui
                  self.ordres_achat = []
                  self.ordres_vente = []
                  self.transactions = []
                  self.lire_ordres('/Users/albanhoerdt/Documents/Cours Dauphine/L3/S2/Python/Projet/Donnees_OrderBook')
                  self.auto_executing = False  # Variable pour activer/désactiver le mode continu
      </code></pre>
          </section>
          <section id="Gestion-des-Ordres" class="level2">
              <h2 class="anchored" data-anchor-id="Gestion-des-Ordres">b. Gestion des Ordres</h2>
              <p>Cette fonction, toggle_auto_executing, est une pièce essentielle de notre application de gestion des ordres. Voici un résumé de son fonctionnement. Elle permet de basculer entre l'activation et la désactivation du mode d'exécution automatique des ordres. Lorsqu'elle est appelée, elle inverse simplement l'état actuel du mode automatique en basculant la valeur de self.auto_executing. Si le mode était activé, il serait désactivé et vice versa. Si le mode automatique est activé (self.auto_executing est True), la fonction effectue deux actions importantes. Elle appelle self.execute_continuously(), une méthode chargée d'exécuter les ordres en continu à intervalles réguliers, assurant ainsi que les transactions sont traitées en temps réel. Elle lance également immédiatement self.generate_orders_periodically(), une méthode destinée à démarrer la génération périodique de nouveaux ordres. Cela peut être utile pour assurer un flux constant d'ordres dans l'application. En revanche, si le mode automatique est désactivé, la fonction ne prend aucune action supplémentaire, mais elle pourrait être étendue à l'avenir pour inclure des fonctionnalités d'arrêt du processus, comme indiqué par le commentaire.</p>
          </section>
          <section id="Activation-mode-continu" class="level2">
              <h2 class="anchored" data-anchor-id="Activation-mode-continu">c. Activation mode continu </h2>
              <pre><code class="language-python"> def toggle_auto_executing(self):
              self.auto_executing = not self.auto_executing
              if self.auto_executing:
                  self.execute_continuously()
                  self.generate_orders_periodically()  # Appel immédiat pour démarrer la génération des ordres
              else:
                  # Ajouter des mesures pour arrêter le processus si nécessaire
                  pass
      </code></pre>
          </section>
          <section id="Méthode-continu" class="level3">
              <h2 class="anchored" data-anchor-id="Méthode-continu">Méthode continu</h2>
              <p>On a ensuite la méthode, execute_continuously, assure une exécution continue des ordres à intervalles réguliers tant que le mode d'exécution automatique est activé. Elle vérifie d'abord si le mode automatique est activé. Si tel est le cas, elle lance l'exécution des ordres en appelant la méthode executer_ordres(). Ensuite, elle utilise self.gui.master.after(1000, self.execute_continuously) pour planifier un rappel de la méthode après une seconde (1000 millisecondes), assurant ainsi une exécution périodique des ordres. Ce processus se poursuit tant que le mode automatique reste activé, garantissant un flux continu d'activité de trading dans notre application.</p>
          <pre><code class="language-python">def execute_continuously(self):
              if self.auto_executing:
                  self.executer_ordres()
                  self.gui.master.after(1000, self.execute_continuously)
          </code></pre>
          </section>
      </section>
<div class="container">
       <section id="lecture-des-ordres" class="level2">
           <h1>Lecture des ordres</h1>
           <hr>
           <section id="methode-lire_ordres" class="level2">
               <h2 class="anchored" data-anchor-id="methode-lire_ordres">a. Méthode lire_ordres</h2>
               <p>La méthode lire_ordres est une fonction clé de notre système de gestion d'ordres. Elle ouvre le fichier spécifié, parcourt ses lignes et extrait les détails de chaque ordre, limitant la lecture à 40 ordres maximum. Pour chaque ligne, elle détermine le type d'ordre (achat ou vente), l'identifiant, la référence de l'actif, le prix et la quantité. Ces données sont utilisées pour ajouter les ordres au carnet d'ordres via la méthode ajouter_ordre, garantissant que l'application démarre avec un ensemble initial d'ordres prêts à être traités. Ainsi, cette méthode assure un chargement efficace des données d'ordres, élément crucial pour le bon fonctionnement de notre système de trading.</p>
               <pre><code class="language-python">def lire_ordres(self, filepath):
       with open(filepath, 'r') as file:
           for i, line in enumerate(file):
               if i >= 40:
                   break
               parts = line.strip().split(',')
               type_ordre = 'achat' if parts[0] == 'B' else 'vente'
               id_ordre = int(parts[1])
               ref_actif = parts[2].strip('"')
               prix = float(parts[3])
               quantite = int(parts[4]) if len(parts) > 4 else 1
               self.ajouter_ordre(type_ordre, id_ordre, ref_actif, prix, quantite)
   </code></pre>
           </section>
       </section>
       <section id="generation-des-taker-et-des-order" class="level2">
           <h1>Génération des taker et des order</h1>
           <hr>
           <section id="methode-taker" class="level2">
               <h2 class="anchored" data-anchor-id="methode-taker">a. Méthode taker</h2>
               <p>La méthode generate_taker_order crée des ordres de type "taker" de manière aléatoire pour simuler des transactions sur le marché. Elle choisit aléatoirement une référence d'actif parmi une liste prédéfinie et détermine aléatoirement si l'ordre sera un achat ou une vente. Si c'est un achat et qu'il existe des ordres de vente disponibles, il fixe le prix d'achat légèrement au-dessus du minimum du marché et génère une quantité aléatoire. Ensuite, il ajoute cet ordre au carnet d'ordres. Si le mode d'exécution automatique est activé, il exécute immédiatement les ordres ajoutés. De même, s'il s'agit d'une vente et qu'il existe des ordres d'achat disponibles, il fixe le prix de vente légèrement en dessous du maximum du marché et génère une quantité aléatoire, puis ajoute cet ordre au carnet d'ordres. Encore une fois, s'il est en mode d'exécution automatique, il exécute immédiatement les ordres ajoutés. Cette méthode simule la prise de décision aléatoire des acteurs sur le marché et leur interaction en générant des ordres de taker basés sur des conditions aléatoires prédéfinies.</p>
               <pre><code class="language-python">def generate_taker_order(self):
       reference = random.choice(['30501', '31601', '31502'])
       order_type = random.choice(['achat', 'vente'])
       if order_type == 'achat' and self.ordres_vente:
           # Taker achète à un prix légèrement supérieur au minimum du marché
           prix_achat = max((ordre['prix'] for ordre in self.ordres_vente), default=10) + random.uniform(1, 100)
           prix_achat = round(prix_achat, 1)
           quantite_achat = random.randint(1, 2000)
           self.ajouter_ordre('achat', len(self.ordres_achat) + 1, reference, prix_achat, quantite_achat)
           if self.auto_executing:  # Exécute les ordres immédiatement si en mode continu
               self.executer_ordres()
       elif order_type == 'vente' and self.ordres_achat:
           # Taker vend à un prix légèrement inférieur au maximum du marché
           prix_vente = min((ordre['prix'] for ordre in self.ordres_achat), default=10) - random.uniform(1, 100)
           prix_vente = round(prix_vente, 1)
           quantite_vente = random.randint(1, 2000)
           self.ajouter_ordre('vente', len(self.ordres_vente) + 1, reference, prix_vente, quantite_vente)
           if self.auto_executing:  # Exécute les ordres immédiatement si en mode continu
               self.executer_ordres()
   </code></pre>
           </section>
           <section id="methode-maker" class="level2">
               <h2 class="anchored" data-anchor-id="methode-maker">b. Méthode maker</h2>
               <p>La méthode generate_maker_order crée des ordres de type "maker" de manière aléatoire pour simuler des transactions sur le marché, elle est quasiment similaire à la méthode précédente, du moins sur le fonctionnement. Elle sélectionne aléatoirement une référence d'actif parmi une liste prédéfinie et détermine aléatoirement si l'ordre sera un achat ou une vente. Si c'est un achat et qu'il existe des ordres de vente disponibles, elle fixe le prix d'achat légèrement en dessous du minimum du marché et génère une quantité aléatoire. Ensuite, elle ajoute cet ordre au carnet d'ordres. Si le mode d'exécution automatique est activé, elle exécute immédiatement les ordres ajoutés. De même, si c'est une vente et qu'il existe des ordres d'achat disponibles, elle fixe le prix de vente légèrement au-dessus du maximum du marché, génère une quantité aléatoire, puis ajoute cet ordre au carnet d'ordres. Encore une fois, si le mode d'exécution automatique est activé, elle exécute immédiatement les ordres ajoutés. Cette méthode simule le comportement des acteurs du marché qui ajoutent des liquidités en créant des ordres de maker basés sur des conditions aléatoires prédéfinies.</p>
               <pre><code class="language-python">def generate_maker_order(self):
       reference = random.choice(['30501', '31601', '31502'])
       order_type = random.choice(['achat', 'vente'])
       if order_type == 'achat' and self.ordres_vente:
           # Maker achète à un prix légèrement inférieur au minimum du marché
           prix_achat = min((ordre['prix'] for ordre in self.ordres_vente), default=10) - random.uniform(1, 100)
           prix_achat = round(prix_achat, 1)
           quantite_achat = random.randint(1, 2000)
           self.ajouter_ordre('achat', len(self.ordres_achat) + 1, reference, prix_achat, quantite_achat)
           if self.auto_executing:  # Exécute les ordres immédiatement si en mode continu
               self.executer_ordres()
       elif order_type == 'vente' and self.ordres_achat:
           # Maker vend à un prix légèrement supérieur au maximum du marché
           prix_vente = max((ordre['prix'] for ordre in self.ordres_achat), default=10) + random.uniform(1, 100)
           prix_vente = round(prix_vente, 1)
           quantite_vente = random.randint(1, 2000)
           self.ajouter_ordre('vente', len(self.ordres_vente) + 1, reference, prix_vente, quantite_vente)
           if self.auto_executing:  # Exécute les ordres immédiatement si en mode continu
               self.executer_ordres()
   </code></pre>
           </section>
           <section id="methode-ajouter_ordre" class="level1">
               <h1 class="anchored" data-anchor-id="methode-ajouter_ordre">Méthode ajouter_ordre</h1>
               <p>La méthode ajouter_ordre gère l'ajout d'un nouvel ordre au carnet d'ordres. Elle prend en paramètres le type d'ordre (achat ou vente), l'identifiant de l'ordre, la référence de l'actif, le prix et la quantité. Avant d'ajouter l'ordre, elle normalise le type d'ordre en le mettant en minuscules. Ensuite, elle détermine le numéro d'ordre suivant en trouvant le maximum des identifiants d'ordres existants dans les listes d'ordres d'achat et de vente, puis elle incrémente ce numéro. Si la quantité de l'ordre est supérieure à zéro, elle crée un dictionnaire représentant l'ordre avec les détails fournis. Selon le type d'ordre, elle ajoute cet ordre à la liste appropriée (achat ou vente), trie ensuite les listes par identifiant d'ordre, et met à jour l'affichage du carnet d'ordres dans l'interface graphique. Cette méthode assure donc l'ajout correct et la mise à jour des ordres dans le carnet d'ordres, maintenant ainsi une représentation précise et à jour de l'état du marché.</p>
               <pre><code class="language-python"> def ajouter_ordre(self, type_ordre, id_ordre, ref_actif, prix, quantite):
       type_ordre = type_ordre.lower()
   
       max_order_number = max(
           max((ordre['id_ordre'] for ordre in self.ordres_achat), default=0),
           max((ordre['id_ordre'] for ordre in self.ordres_vente), default=0)
       )
       next_order_number = max_order_number + 1
   
       if quantite > 0:
           ordre = {'type': type_ordre, 'id_ordre': next_order_number, 'ref_actif': ref_actif, 'prix': prix, 'quantite': quantite}
           if type_ordre == 'achat':
               self.ordres_achat.append(ordre)
               self.ordres_achat.sort(key=lambda x: x['id_ordre'])
           else:
               self.ordres_vente.append(ordre)
               self.ordres_vente.sort(key=lambda x: x['id_ordre'])
           self.gui.afficher_carnet(self.ordres_achat, self.ordres_vente)
   </code></pre>
           </section>
       </section>
       <section id="Execution-des-ordres" class="level1">
           <h1>Exécution des ordres</h1>
           <hr>
           <section id="methode-execution-logique" class="level2">
               <h2 class="anchored" data-anchor-id="methode-execution-logique">a. Méthode exécution logique</h2>
               <p>La méthode executer_ordres_logique prend en charge la logique d'exécution des ordres dans le carnet d'ordres. Elle commence par trier les listes d'ordres d'achat et de vente en fonction du prix, les achats par ordre décroissant et les ventes par ordre croissant. Ensuite, elle parcourt les listes pour trouver les transactions possibles en comparant les prix et les références d'actif des ordres. Si une transaction est possible, elle détermine la quantité à exécuter, enregistre la transaction dans l'historique des transactions, met à jour les quantités des ordres impliqués et supprime les ordres épuisés. Après avoir traité toutes les transactions possibles, elle met à jour l'affichage du carnet d'ordres dans l'interface graphique et ouvre une fenêtre affichant l'historique des transactions. Cette méthode assure l'exécution correcte des ordres en fonction de leur prix et de leur quantité, tout en maintenant un suivi précis des transactions effectuées.</p>
               <pre><code class="language-python"> def executer_ordres_logique(self):
       achats = sorted(self.ordres_achat[:], key=lambda x: x['prix'], reverse=True)
       ventes = sorted(self.ordres_vente[:], key=lambda x: x['prix'])
       for achat in achats:
           if achat['quantite'] == 0:
               continue
           for vente in ventes:
               if vente['quantite'] == 0:
                   continue
               if achat['ref_actif'] == vente['ref_actif'] and achat['prix'] >= vente['prix']:
                   quantite_executee = min(achat['quantite'], vente['quantite'])
                   transaction_prix = vente['prix']
                   self.transactions.append({
                       'achat_id': achat['id_ordre'],
                       'vente_id': vente['id_ordre'],
                       'prix': transaction_prix,
                       'quantite': quantite_executee,
                       'ref_actif': achat['ref_actif']
                   })
                   achat['quantite'] -= quantite_executee
                   vente['quantite'] -= quantite_executee
                   if vente['quantite'] == 0:
                       self.ordres_vente.remove(vente)
                   if achat['quantite'] == 0:
                       self.ordres_achat.remove(achat)
                       break
       self.gui.afficher_carnet(self.ordres_achat, self.ordres_vente)
       self.gui.ouvrir_historique(self.transactions)
   </code></pre>
           </section>
           <section id="Execution" class="level2">
               <h2 class="anchored" data-anchor-id="Execution">b. Exécution</h2>
               <p>La méthode executer_ordres est responsable de l'exécution des ordres. Elle commence par appeler la méthode executer_ordres_logique pour gérer la logique d'exécution des ordres. Ensuite, elle met à jour l'affichage du carnet d'ordres dans l'interface graphique en affichant les listes d'ordres d'achat et de vente mises à jour. Enfin, elle ouvre une fenêtre affichant l'historique des transactions. Cette méthode coordonne le processus d'exécution des ordres et assure la mise à jour de l'affichage de l'état du carnet d'ordres et de l'historique des transactions.</p>
               <pre><code class="language-python">     
       def executer_ordres(self):
           self.executer_ordres_logique()
           self.gui.afficher_carnet(self.ordres_achat, self.ordres_vente)
           self.gui.ouvrir_historique(self.transactions)
       </code></pre>
           </section>
       </section>
          <section id="determination-des-tick-et-des-lot" class="level2">
              <h2>c. Détermination des ticks et des lots</h2>
              <hr>
              <section id="methode-calculer_tick_et_lot" class="level3">
                  <h3 class="anchored" data-anchor-id="methode-calculer_tick_et_lot"> Méthode calculer_tick_et_lot</h3>
                  <p>La fonction calculer_tick_et_lot prend en entrée une référence d'actif et cherche ses données de tick et de lot dans un fichier spécifié, ici Donnees_Tick_Lot. Elle ouvre le fichier, parcourt chaque ligne, et sépare les éléments en parties. Si la référence d'actif correspond à celle trouvée dans une ligne du fichier, la fonction extrait les valeurs du tick et du lot associé à cette référence. Ensuite, elle retourne ces valeurs. Si aucune correspondance n'est trouvée, elle retourne "N/A" pour indiquer que les données n'ont pas été trouvées. Cette fonction récupère les informations sur le tick et le lot d'un actif à partir d'un fichier et les renvoie pour utilisation.</p>
                  <pre><code class="language-python"> def calculer_tick_et_lot(self, ref_actif):
          filepath = "/Users/albanhoerdt/Documents/Cours Dauphine L3/S2/Python/Projet/Donnees_Tick_Lot"
          with open(filepath, 'r') as file:
              for line in file:
                  parts = line.strip().split(',')
                  if parts[0] == ref_actif:
                      lot = float(parts[1])
                      tick = float(parts[2])
                      return tick, lot
          return "N/A", "N/A"
          </code></pre>
              </section>
   <section id="seconde-classe-carnetordresgui" class="level1">
               <h1 class="anchored" data-anchor-id="seconde-classe-carnetordresgui"> Seconde Classe CarnetOrdresGUI</h1>
               <p>Dans la seconde classe CarnetOrdresGUI nous allons créer l’interface, en voici un aperçu, nous expliquons dans la suite sa création et son utilisation.</p>
               <img width="495" alt="Capture d’écran 2024-04-26 à 20 28 33" src="https://github.com/AlHoer/Carnet-d-ordre/assets/163281343/1663689a-e5c4-43ba-9aae-a94b4194f673">
               <section id="code-de-la-classe-carnetordresgui" class="level2">
                   <h2 class="anchored" data-anchor-id="code-de-la-classe-carnetordresgui"> Code de la Classe CarnetOrdresGUI</h2>
                   <pre><code class="language-python">class CarnetOrdresGUI:
       def __init__(self, master):
           self.master = master
           master.title("Carnet d'ordres")
           self.setup_trees()
           self.setup_form()
       </code></pre>
               </section>
           </section>
           <section id="methode-setup_trees" class="level2">
               <h2 class="anchored" data-anchor-id="methode-setup_trees">a. Méthode setup_trees</h2>
               <p>La méthode setup_trees de la classe CarnetOrdresGUI crée une interface pour afficher les ordres d'achat et de vente dans deux tableaux distincts. Elle crée un cadre contenant deux étiquettes "Achat" et "Vente", puis crée deux tableaux d'affichage des ordres d'achat et de vente à gauche et à droite, respectivement. Chaque tableau comporte quatre colonnes : "Ordre", "Référence", "Prix" et "Quantité". Les ordres sont affichés dans ces tableaux avec les détails appropriés. Enfin, elle initialise un objet CarnetOrdres pour gérer les données d'ordres.</p>
               <pre><code class="language-python">def setup_trees(self):
       frame = tk.Frame(self.master)
       frame.pack(side='top', fill=tk.X)
       # Label "Achat" à gauche
       tk.Label(frame, text="Achat", font=('Arial', 14)).pack(side='left', padx=10)
       # Label "Vente" à droite
       tk.Label(frame, text="Vente", font=('Arial', 14)).pack(side='right', padx=10)
       self.tree_achat = ttk.Treeview(frame, columns=('Ordre', 'Référence', 'Prix', 'Quantité'), show='headings')
       self.tree_achat.pack(side='left', fill=tk.BOTH, expand=True)
       self.tree_vente = ttk.Treeview(frame, columns=('Ordre', 'Référence', 'Prix', 'Quantité'), show='headings')
       self.tree_vente.pack(side='right', fill=tk.BOTH, expand=True)
       for tree in (self.tree_achat, self.tree_vente):
           for col in tree['columns']:
               tree.heading(col, text=col)
               tree.column(col, width=100)
       self.carnet = CarnetOrdres(self)
       </code></pre>
           </section>
           <section id="methode-setup_form" class="level2">
               <h2 class="anchored" data-anchor-id="methode-setup_form">b. Méthode setup_form</h2>
               <p>La méthode setup_form de la classe CarnetOrdresGUI crée une interface pour saisir de nouveaux ordres. Elle crée un cadre de formulaire contenant des champs pour saisir le type d'ordre, le prix, la quantité et la référence. De plus, elle initialise des variables pour stocker les valeurs saisies dans ces champs. Deux étiquettes "Tick" et "Lot" sont également configurées au-dessus des entrées de formulaire pour afficher ces informations, initialement définies comme "N/A". 
                   Le deuxième bloc de code crée des étiquettes, des champs de saisie et des boutons pour saisir et gérer les ordres dans l'interface utilisateur. Les étiquettes définissent les types d'informations à saisir, comme le type d'ordre (achat/vente), le prix, la quantité et la référence. Les champs de saisie sont associés à des variables qui stockent les valeurs saisies par l'utilisateur. Des boutons sont également ajoutés pour ajouter un nouvel ordre, exécuter les ordres et afficher l'historique des transactions. De plus, un champ de saisie est ajouté pour spécifier la référence utilisée dans le calcul du tick et du lot, avec un bouton pour afficher ces valeurs.
                   Le troisième et quatrième bloc ajoute un champ de saisie pour spécifier le numéro d'ordre à supprimer et des boutons radio pour sélectionner le type d'ordre à supprimer (achat ou vente). Un bouton "Supprimer Ordre" est également ajouté, qui déclenche une fonction pour supprimer l'ordre spécifié en fonction du numéro et du type sélectionnés.
                   Enfin le dernier bloc ajoute un champ de saisie pour spécifier le numéro d'ordre à supprimer et des boutons radio pour sélectionner le type d'ordre à supprimer (achat ou vente). Un bouton "Supprimer Ordre" est également ajouté, qui déclenche une fonction pour supprimer l'ordre spécifié en fonction du numéro et du type sélectionnés.
               </p>
               <pre><code class="language-python"> def setup_form(self):
       form_frame = tk.Frame(self.master)
       form_frame.pack(side='top', fill=tk.X)
       self.type_ordre_var = tk.StringVar()
       self.prix_var = tk.StringVar()
       self.quantite_var = tk.StringVar()
       self.reference_var = tk.StringVar()
       # Configuration des labels pour le tick et le lot au-dessus des entrées de formulaire
       self.tick_label = tk.Label(form_frame, text="Tick: N/A")
       self.tick_label.grid(row=2, column=3, columnspan=3, sticky='ew')  # Prend toute la largeur
       self.lot_label = tk.Label(form_frame, text="Lot: N/A")
       self.lot_label.grid(row=3, column=3, columnspan=3, sticky='ew')  # Prend toute la largeur
       
       
       tk.Label(form_frame, text="Type d'Ordre (Achat/Vente):").grid(row=0, column=0)
       tk.Entry(form_frame, textvariable=self.type_ordre_var).grid(row=0, column=1)
       tk.Label(form_frame, text="Prix:").grid(row=1, column=0)
       tk.Entry(form_frame, textvariable=self.prix_var).grid(row=1, column=1)
       tk.Label(form_frame, text="Quantité:").grid(row=2, column=0)
       tk.Entry(form_frame, textvariable=self.quantite_var).grid(row=2, column=1)
       tk.Label(form_frame, text="Référence:").grid(row=3, column=0)
       tk.Entry(form_frame, textvariable=self.reference_var).grid(row=3, column=1)
       tk.Button(form_frame, text="Ajouter Ordre", command=self.ajouter_ordre_new).grid(row=4, column=0, columnspan=2)
       tk.Button(form_frame, text="Exécuter Ordres", command=self.carnet.executer_ordres).grid(row=5, column=0, columnspan=2)
       tk.Button(form_frame, text="Historique", command=self.ouvrir_historique).grid(row=6, column=0, columnspan=2)
        # Ajout d'un champ pour la référence du calcul de tick et lot
       tk.Label(form_frame, text="Ref pour Tick/Lot:").grid(row=5, column=3)
       self.ref_tick_lot_var = tk.StringVar()
       tk.Entry(form_frame, textvariable=self.ref_tick_lot_var).grid(row=5, column=4)
       tk.Button(form_frame, text="Valeur Tick et Lot", command=self.afficher_tick_lot).grid(row=4, column=4)
       
       # Add entry and button for order deletion
       self.delete_order_var = tk.StringVar()
       self.order_type_var = tk.StringVar()
   
       tk.Label(form_frame, text="Numéro d'Ordre à supprimer:").grid(row=7, column=0)
       tk.Entry(form_frame, textvariable=self.delete_order_var).grid(row=7, column=1)
   
       # Radiobuttons to select the type of order to delete
       tk.Radiobutton(form_frame, text="Achat", variable=self.order_type_var, value="achat").grid(row=7, column=2)
       tk.Radiobutton(form_frame, text="Vente", variable=self.order_type_var, value="vente").grid(row=7, column=3)
   
       tk.Button(form_frame, text="Supprimer Ordre", command=self.supprimer_ordre).grid(row=7, column=4)
       
       # Bouton pour activer/désactiver le mode continu
       self.continuous_button = tk.Button(form_frame, text="Mode Continu", command=self.toggle_continuous)
       self.continuous_button.grid(row=1, column=4, columnspan=2)
       
       # Ajout des boutons pour générer des ordres Taker et Maker
       tk.Button(form_frame, text="Générer Ordre Taker", command=self.carnet.generate_taker_order).grid(row=9, column=1)
       tk.Button(form_frame, text="Générer Ordre Maker", command=self.carnet.generate_maker_order).grid(row=9, column=4)
   
   </code></pre>
           </section>
           <section id="methode-toggle_continuous" class="level2">
               <h2 class="anchored" data-anchor-id="methode-toggle_continuous">c. Méthode toggle_continuous</h2>
               <p>Cette fonction permet de basculer entre le mode d'exécution continue et le mode d'exécution manuelle des ordres dans l'interface graphique. Lorsque le bouton associé est activé, la fonction vérifie l'état actuel du mode d'exécution automatique dans l'objet carnet. Si le mode automatique est activé, la fonction lance l'exécution continue des ordres à l'aide de la méthode execute_continuously() et met à jour le libellé du bouton pour indiquer qu'il peut être utilisé pour arrêter le mode continu. Si le mode automatique est désactivé, le libellé du bouton est rétabli pour indiquer que le mode continu peut être activé.</p>
               <pre><code class="language-python"> def toggle_continuous(self):
       self.carnet.toggle_auto_executing()
       if self.carnet.auto_executing:
           self.carnet.execute_continuously()
           self.continuous_button.config(text="Arrêter Mode Continu")
       else:
           self.continuous_button.config(text="Mode Continu")
   </code></pre>
           </section>
           <section id="methode-setup_trees" class="level2">
               <h2 class="anchored" data-anchor-id="methode-setup_trees">a. Méthode setup_trees</h2>
               <p>La méthode setup_trees de la classe CarnetOrdresGUI crée une interface pour afficher les ordres d'achat et de vente dans deux tableaux distincts. Elle crée un cadre contenant deux étiquettes "Achat" et "Vente", puis crée deux tableaux d'affichage des ordres d'achat et de vente à gauche et à droite, respectivement. Chaque tableau comporte quatre colonnes : "Ordre", "Référence", "Prix" et "Quantité". Les ordres sont affichés dans ces tableaux avec les détails appropriés. Enfin, elle initialise un objet CarnetOrdres pour gérer les données d'ordres.</p>
               <pre><code class="language-python">def setup_trees(self):
       frame = tk.Frame(self.master)
       frame.pack(side='top', fill=tk.X)
       # Label "Achat" à gauche
       tk.Label(frame, text="Achat", font=('Arial', 14)).pack(side='left', padx=10)
       # Label "Vente" à droite
       tk.Label(frame, text="Vente", font=('Arial', 14)).pack(side='right', padx=10)
       self.tree_achat = ttk.Treeview(frame, columns=('Ordre', 'Référence', 'Prix', 'Quantité'), show='headings')
       self.tree_achat.pack(side='left', fill=tk.BOTH, expand=True)
       self.tree_vente = ttk.Treeview(frame, columns=('Ordre', 'Référence', 'Prix', 'Quantité'), show='headings')
       self.tree_vente.pack(side='right', fill=tk.BOTH, expand=True)
       for tree in (self.tree_achat, self.tree_vente):
           for col in tree['columns']:
               tree.heading(col, text=col)
               tree.column(col, width=100)
       self.carnet = CarnetOrdres(self)
   </code></pre>
           </section>
           <section id="methode-supprimer_ordre" class="level2">
               <h2 class="anchored" data-anchor-id="methode-supprimer_ordre">d. Méthode supprimer_ordre</h2>
               <p>Cette fonction supprime un ordre spécifié par son numéro d'identification et son type (achat ou vente). Elle récupère d'abord l'identifiant de l'ordre à partir de la variable associée à l'entrée de suppression. Ensuite, en fonction du type d'ordre sélectionné (achat ou vente), elle filtre les listes d'ordres correspondantes dans l'objet carnet, en ne gardant que les ordres dont l'identifiant est différent de celui à supprimer. Enfin, elle met à jour l'affichage du carnet d'ordres dans l'interface graphique en appelant la méthode afficher_carnet(). Un message de confirmation est également affiché pour informer l'utilisateur du succès de l'opération.</p>
               <pre><code class="language-python">def supprimer_ordre(self):
       order_id = int(self.delete_order_var.get())
       order_type = self.order_type_var.get()
   
       if order_type == "achat":
           self.carnet.ordres_achat = [ordre for ordre in self.carnet.ordres_achat if ordre['id_ordre'] != order_id]
       elif order_type == "vente":
           self.carnet.ordres_vente = [ordre for ordre in self.carnet.ordres_vente if ordre['id_ordre'] != order_id]
   
       self.afficher_carnet(self.carnet.ordres_achat, self.carnet.ordres_vente)
       tkinter.messagebox.showinfo("Success", f"Ordre {order_id} supprimé.")
   </code></pre>
           </section>
           </section>
           <section id="methode-afficher_tick_et_lot" class="level2">
               <h2 class="anchored" data-anchor-id="methode-afficher_tick_et_lot">e. Méthode afficher tick et lot</h2>
               <p>Cette fonction affiche le tick et le lot associés à une référence d'actif spécifiée dans l'interface graphique. Elle récupère d'abord la référence d'actif à partir de la variable associée à l'entrée correspondante. Ensuite, elle utilise la méthode calculer_tick_et_lot() de l'objet carnet pour obtenir les valeurs du tick et du lot pour cette référence d'actif. Enfin, elle met à jour le texte des labels d'affichage du tick et du lot dans l'interface graphique avec ces valeurs.</p>
               <pre><code class="language-python">def afficher_tick_lot(self):
       ref_actif = self.ref_tick_lot_var.get()
       tick, lot = self.carnet.calculer_tick_et_lot(ref_actif)
       self.tick_label.config(text=f"Tick pour {ref_actif}: {tick}")
       self.lot_label.config(text=f"Lot pour {ref_actif}: {lot}")
   </code></pre>
           </section>
           </section>
           <section id="methode-ajouter_ordre_new" class="level2">
               <h2 class="anchored" data-anchor-id="methode-ajouter_ordre_new">f. Méthode-ajouter_ordre_new</h2>
               <p>Cette fonction tente d'ajouter un nouvel ordre en récupérant les valeurs nécessaires à partir des variables associées aux différents champs du formulaire. Si les valeurs récupérées sont valides, elle génère un nouvel identifiant d'ordre en fonction du nombre d'ordres existants, puis utilise la méthode ajouter_ordre() de l'objet carnet pour ajouter l'ordre. Ensuite, si le mode d'exécution automatique est activé, elle exécute immédiatement les ordres nouvellement ajoutés. En cas d'erreur de valeur lors de la conversion des données d'entrée en nombres, elle affiche une boîte de dialogue d'erreur.</p>
               <pre><code class="language-python">def ajouter_ordre_new(self):
       try:
           type_ordre = self.type_ordre_var.get()
           prix = float(self.prix_var.get())
           quantite = int(self.quantite_var.get())
           reference = self.reference_var.get()
           id_ordre = len(self.carnet.ordres_achat) + len(self.carnet.ordres_vente) + 1
           self.carnet.ajouter_ordre(type_ordre, id_ordre, reference, prix, quantite)
           # Après l'ajout d'un nouvel ordre, tester s'il faut exécuter les ordres
           if self.carnet.auto_executing:
               self.carnet.executer_ordres()
       except ValueError:
           tkinter.messagebox.showerror("Erreur", "Veuillez entrer des valeurs valides.")
   </code></pre>
           </section>
               </section>
           <section id="methode-afficher_carnet" class="level2">
               <h2 class="anchored" data-anchor-id="methode-afficher_carnet">g. Méthode afficher_carnet</h2>
               <p>Cette fonction met à jour l'affichage du carnet d'ordres en supprimant tous les éléments existants dans les arbres de visualisation des ordres d'achat et de vente, puis en insérant les nouvelles données d'ordres fournies dans les arguments ordres_achat et ordres_vente. Chaque ordre est représenté par une ligne dans l'arbre correspondant, affichant les détails tels que l'identifiant de l'ordre, la référence de l'actif, le prix et la quantité.</p>
               <pre><code class="language-python"> def afficher_carnet(self, ordres_achat, ordres_vente):
       for tree in (self.tree_achat, self.tree_vente):
           tree.delete(*tree.get_children())
       for ordre in ordres_achat:
           self.tree_achat.insert('', 'end', values=(ordre['id_ordre'], ordre['ref_actif'], ordre['prix'], ordre['quantite']))
       for ordre in ordres_vente:
           self.tree_vente.insert('', 'end', values=(ordre['id_ordre'], ordre['ref_actif'], ordre['prix'], ordre['quantite']))
   </code></pre>
           </section>
           <section id="methode-ouvrir_historique" class="level2">
               <h2 class="anchored" data-anchor-id="methode-ouvrir_historique">h. Méthode ouvrir_historique</h2>
               <p>Cette fonction crée une nouvelle fenêtre pour afficher l'historique des transactions. Elle crée un widget Treeview pour afficher les données de l'historique sous forme de tableau. Les colonnes du tableau représentent les détails de chaque transaction, tels que les identifiants d'achat et de vente, la référence, le prix et la quantité. Les données sont extraites de l'attribut transactions de l'objet CarnetOrdres associé.</p>
               <pre><code class="language-python"> def ouvrir_historique(self):
       history_window = tk.Toplevel(self.master)
       history_window.title("Historique des Transactions")
       tree = ttk.Treeview(history_window, columns=('Achat ID', 'Vente ID', 'Référence', 'Prix', 'Quantité'), show='headings')
       tree.pack(expand=True, fill=tk.BOTH)
       for col in tree['columns']:
           tree.heading(col, text=col)
           tree.column(col, width=100)
       for transaction in self.carnet.transactions:
           tree.insert('', 'end', values=(transaction['achat_id'], transaction['vente_id'], transaction['ref_actif'], transaction['prix'], transaction['quantite']))
   </code></pre>
           </section>
       <section id="methode-initialisation-interface" class="level1">
               <h1 class="anchored" data-anchor-id="methode-initialisation-interface">Méthode Initialisation Interface</h1>
               <p>Cette fonction initialise l'interface graphique en créant une instance de la classe tk.Tk() pour la fenêtre principale. Ensuite, elle crée une instance de CarnetOrdresGUI, la classe qui gère l'interface graphique de l'application. Enfin, elle démarre la boucle principale de l'interface graphique avec la méthode mainloop() de l'objet racine (root). La condition if __name__ == '__main__': garantit que le script est exécuté en tant que programme principal.</p>
               <pre><code class="language-python"> def main():
       root = tk.Tk()
       app = CarnetOrdresGUI(root)
       root.mainloop()
   
   if __name__ == '__main__':
       main()
       </code></pre>
           </section>
          <section id="Conclusion" class="level1">
                  <h1 class="anchored" data-anchor-id="Conclusion">Conclusion</h1>
   <p>Le projet de carnet d'ordres que nous avons développé est un exemple fonctionnel d'une application simple permettant de gérer des ordres d'achat et de vente sur un marché financier simulé. Voici quelques points à retenir de ce projet :<p>
   <p>- **Fonctionnalités principales** : L'application permet d'ajouter des ordres d'achat et de vente, de les exécuter manuellement ou automatiquement en mode continu, et de visualiser le carnet d'ordres ainsi que l'historique des transactions.<p>
   <p>- **Interface graphique conviviale** : Nous avons utilisé Tkinter pour créer une interface utilisateur simple mais efficace, avec des boutons et des champs pour interagir avec l'application de manière intuitive.<p>
   <p>- **Logique d'exécution des ordres** : Les ordres sont exécutés en respectant les règles spécifiées, notamment en s'assurant que les ordres d'achat correspondent à des ordres de vente existants au niveau des prix, et vice versa.<p>
   <p>- **Mode continu** : L'application offre la possibilité de fonctionner en mode continu, où de nouveaux ordres sont générés périodiquement et exécutés automatiquement.<p>
   <p>- **Gestion des données** : Les données des ordres et des transactions sont stockées dans des structures de données appropriées, et les transactions sont enregistrées pour consultation ultérieure.<p>
   <p>En conclusion, ce projet fournit une base solide pour une application de trading simplifiée. Il pourrait être étendu avec des fonctionnalités supplémentaires telles que la gestion des utilisateurs, l'authentification, la visualisation graphique des données, etc., pour en faire une solution plus complète et robuste.</p>
       </section>
</div>
<div class="footer">
   Projet Carnet d'Ordre - Développé par Alban Hoerdt & Lucien Durand
</div>

</body>
</html>
