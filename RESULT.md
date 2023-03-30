1. установлен minikube, дополнительный, чтобы не удалять более новый, который мне нужен на хосте

![img_15.png](img_15.png)

![img_16.png](img_16.png)

2. создаем неймспейсы для операторов

![img_2.png](img_2.png)

3. устанавливаем istioctl

и добавляем в .bashrc строку

`
export PATH=$HOME/.istioctl/bin:$PATH
`

![img_12.png](img_12.png)

4. helm у меня уже был установлен, пользовался ранее

![img_4.png](img_4.png)

5. разворачиваем jaeger

![img_5.png](img_5.png)

![img_6.png](img_6.png)

![img_7.png](img_7.png)

![img_8.png](img_8.png)

6. Разворачиваем Prometheus

![img_9.png](img_9.png)

![img_10.png](img_10.png)

![img_11.png](img_11.png)

7. Разворачиваем Istio

![img_3.png](img_3.png)

![img_13.png](img_13.png)

![img_14.png](img_14.png)

8. Устанавливаем Kiali

![img.png](img.png)

![img_1.png](img_1.png)

![img_17.png](img_17.png)

![img_18.png](img_18.png)

![img_19.png](img_19.png)

9. Собираем две версии приложения

![img_20.png](img_20.png)

![img_21.png](img_21.png)

![img_22.png](img_22.png)

![img_23.png](img_23.png)

10. Готовим и запускаем балансировку двух версий приложения


[манифесты для запуска объектов kubernetes](manifests)

11. Проверка результатов

находим шлюз istio

![img_25.png](img_25.png)

так как никакого ingress внутрь minikube я не настраивал, можно проверить трафик istio просто изнутри кластера кубера, для этого зайдем в кластер командой

`minikube -p minikube-old ssh`

и что-нибудь пошлем в шлюз, можно пинг, можно curl

![img_26.png](img_26.png)

в результате получим [диаграмму](/home/stranger/Изображения/kiali-diagram-result.jpg) в Kilio, отображающую трафик и схему istio

![](/media/stranger/repo/otus-homework-istio/kiali-diagram-result.jpg)

