# sentinelCorp

Dit computer vision model gebruikt sentinel-2 sateliet foto's van [copernicus.eu](https://browser.dataspace.copernicus.eu).
Deze zijn onder andere de True Color en NVDI score. We gebruiken ook een model van Huggingface 🤗 om woonzones te
maskeren bij het gebruiken van dit model (Je kan namelijk geen maïs of andere gewassen groeien op een huis).
 
Het HF model is hier terug te vinden [satelite-terrain-segformer](https://huggingface.co/ZeeeWP/segformer-b0-finetuned-segments-satellite-terrain).

Ons eigen getrained model is gebouwd op de bekende UNet architectuur. Deze had tijdens het trainen en valideren waardes van:

| train_loss | train_mae | val_loss | val_mae |
|------------|-----------|----------|---------|
| 0.0060     |0.0560     | 0.0060   | 0.0620  |

Dat deze waardes zo laag zijn is eigenlijk onverwacht, de trainingsset bestaat maar uit 4 foto's, je zou denken dat de waardes veel hoger zouden liggen!
Het model wordt getrained door de foto's op te delen in kleiner stukken van elke 64x64 pixels. hierdoor hebben we een zeer grote dataset.

Om het model te gebruiken moet je gewoon de model.ipynb file runnen na het aanmaken van een
conda enviroment met behulp van `requirements.txt`. De rest zou zichzelf moeten uitwijzen.

