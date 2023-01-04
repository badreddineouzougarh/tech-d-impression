# tech-d-impression
# Obtenir la couche vecteur
layer = qgis.utils.iface.activeLayer()

# Obtenir le renderer de la couche vecteur
renderer = layer.renderer()

# Boucler sur chaque élément de la couche
for feature in layer.getFeatures():
    # Obtenir le code de l'élément
    code = feature["code"]
   
    # Définir la couleur de l'élément en fonction de son code
    if code == 1:
        color = QColor("red")
    elif code == 2:
        color = QColor("blue")
    else:
        color = QColor("green")
        
    # Créer un symbole de point avec la couleur définie
    symbol = QgsMarkerSymbol.createSimple({'color': '%s,%s,%s' % (color.red(), color.green(), color.blue())})
    
    # Appliquer le symbole à l'élément
    renderer.setSymbol(symbol)

# Mettre à jour la couche vecteur
layer.triggerRepaint()
