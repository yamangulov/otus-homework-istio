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

необходимо также открыть для minikube туннель, иначе не будет доступа снаружи кластера и istio-ingressgateway будет все время в статусе pending

`minikube -p minikube-old tunnel` и через некоторое время ввести пароль root

![img_24.png](img_24.png)

затем дважды проверим работу istio - один раз прямо внутри кластера, зайдя в него по ssh командой minikube -p minikube-old ssh и затем curl на external ip

![img_27.png](img_27.png)

затем проверяем доступ извне кластера по тому же ip

![img_28.png](img_28.png)

а также проверим работу через браузер

![img_29.png](img_29.png)

в результате получим [диаграмму](kiali-diagram-result.jpg) в Kilio, отображающую трафик и схему istio

мы видим на ней два источника - unknown это для случая, когда я курлил сервис изнутри кластера, а именованный источник - для случаев, когда я курлил сервис через istio-ingressgateway

![](kiali-diagram-result.jpg)

