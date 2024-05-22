Se llama de la siguiente forma: 

> [!note] Llamada 
>```py
> from ultralytics import YOLO
>model = YOLO('yolov8n.pt')
model.tune(data='coco8.yaml', epochs=10, iterations=300, optimizer='AdamW', plots=False, save=False, val=False)
> ```


Si no se espesifica el espacio de hiper-parametros los parametros a variar son los siguientes: 

>[!note] Espacio hiperparametros
>```py
>{ 
>"lr0": (1e-5, 1e-1), 
>"lrf": (0.0001, 0.1), 
>"momentum": (0.7, 0.98, 0.3),
>"weight_decay": (0.0, 0.001),
>"warmup_epochs": (0.0, 5.0),
>"warmup_momentum": (0.0, 0.95),
>"box": (1.0, 20.0), 
>"cls": (0.2, 4.0), 
>"dfl": (0.4, 6.0), 
>"hsv_h": (0.0, 0.1), 
>"hsv_s": (0.0, 0.9),
>"hsv_v": (0.0, 0.9),
>"degrees": (0.0, 45.0),
>"translate": (0.0, 0.9), 
>"scale": (0.0, 0.95), 
>"shear": (0.0, 10.0),
>"perspective": (0.0, 0.001), 
>"flipud": (0.0, 1.0), 
>"fliplr": (0.0, 1.0), 
>"bgr": (0.0, 1.0), 
>"mosaic": (0.0, 1.0), 
>"mixup": (0.0, 1.0),
>"copy_paste": (0.0, 1.0)
>}
>```

https://docs.ultralytics.com/yolov5/tutorials/hyperparameter_evolution/


Notas de YOLO 5, `No es identico a como es ahora, pero sirve`: https://docs.ultralytics.com/yolov5/tutorials/hyperparameter_evolution/#3-evolve
