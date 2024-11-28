
Встановлює всі надбудови

### Опис {#synopsis}

Вставляє всі надбудови.

```shell
kubeadm init phase addon all [flags]
```

### Параметри {#options}

<table style="width: 100%; table-layout: fixed;">
    <colgroup>
        <col span="1" style="width: 10px;" />
        <col span="1" />
    </colgroup>
    <tbody>
        <tr>
            <td colspan="2">--apiserver-advertise-address string</td>
        </tr>
        <tr>
            <td></td>
            <td style="line-height: 130%; word-wrap: break-word;"><p>IP-адреса, на якому API-сервер буде оголошувати що віе прослуховує звернення. Якщо не вказано, використовується стандартний мережевий інтерфейс.</p></td>
        </tr>
        <tr>
            <td colspan="2">--apiserver-bind-port int32&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Типово: 6443</td>
        </tr>
        <tr>
            <td></td>
            <td style="line-height: 130%; word-wrap: break-word;"><p>Порт, до якого API-сервер буде привʼязуватися.</p></td>
        </tr>
        <tr>
            <td colspan="2">--config string</td>
        </tr>
        <tr>
            <td></td>
            <td style="line-height: 130%; word-wrap: break-word;"><p>Шлях до конфігураційного файлу kubeadm.</p></td>
        </tr>
        <tr>
            <td colspan="2">--control-plane-endpoint string</td>
        </tr>
        <tr>
            <td></td>
            <td style="line-height: 130%; word-wrap: break-word;"><p>Вказує стабільну IP-адресу або DNS-імʼя для панелі управління.</p></td>
        </tr>
        <tr>
            <td colspan="2">--dry-run</td>
        </tr>
        <tr>
            <td></td>
            <td style="line-height: 130%; word-wrap: break-word;"><p>Не застосовувати жодних змін; просто вивести, що буде зроблено.</p></td>
        </tr>
        <tr>
            <td colspan="2">--feature-gates string</td>
        </tr>
        <tr>
            <td></td>
            <td style="line-height: 130%; word-wrap: break-word;"><p>Набір пар ключ=значення, що описують функціональні можливості для різних функцій. Опції:<br/>
            ControlPlaneKubeletLocalMode=true|false (ALPHA — default=false)<br/>
            EtcdLearnerMode=true|false (BETA — default=true)<br/>
            PublicKeysECDSA=true|false (DEPRECATED — default=false)<br/>
            RootlessControlPlane=true|false (ALPHA — default=false)<br/>
            WaitForAllControlPlaneComponents=true|false (ALPHA — default=false)</p></td>
        </tr>
        <tr>
            <td colspan="2">-h, --help</td>
        </tr>
        <tr>
            <td></td>
            <td style="line-height: 130%; word-wrap: break-word;"><p>Довідка all</p></td>
        </tr>
        <tr>
            <td colspan="2">--image-repository string&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Типово: "registry.k8s.io"</td>
        </tr>
        <tr>
            <td></td>
            <td style="line-height: 130%; word-wrap: break-word;"><p>Вибір реєстру контейнерів для завантаження образів панелі управління</p></td>
        </tr>
        <tr>
            <td colspan="2">--kubeconfig string&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Типово: "/etc/kubernetes/admin.conf"</td>
        </tr>
        <tr>
            <td></td>
            <td style="line-height: 130%; word-wrap: break-word;"><p>Файл kubeconfig, який використовується для спілкування з кластером. Якщо прапорець не встановлено, може буити переглянутий набір стандартних місць для пошуку наявного файлу kubeconfig.</p></td>
        </tr>
        <tr>
            <td colspan="2">--kubernetes-version string&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Типово: "stable-1"</td>
        </tr>
        <tr>
            <td></td>
            <td style="line-height: 130%; word-wrap: break-word;"><p>Вибір конкретної версії Kubernetes для панелі управління.</p></td>
        </tr>
        <tr>
            <td colspan="2">--pod-network-cidr string</td>
        </tr>
        <tr>
            <td></td>
            <td style="line-height: 130%; word-wrap: break-word;"><p>Вказує діапазон IP-адрес для мережі Pod. Якщо встановлено, панель управління автоматично виділить CIDR для кожного вузла.</p></td>
        </tr>
        <tr>
            <td colspan="2">--service-cidr string&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Типово: "10.96.0.0/12"</td>
        </tr>
        <tr>
            <td></td>
            <td style="line-height: 130%; word-wrap: break-word;"><p>Використовуйте альтернативний діапазон IP-адрес для сервісів VIP.</p></td>
        </tr>
        <tr>
            <td colspan="2">--service-dns-domain string&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Типово: "cluster.local"</td>
        </tr>
        <tr>
            <td></td>
            <td style="line-height: 130%; word-wrap: break-word;"><p>Використовуйте альтернативний домен для сервісів, наприклад, "myorg.internal".</p></td>
        </tr>
    </tbody>
</table>

### Параметри успадковані від батьківських команд {#options-inherited-from-parent-commands}

<table style="width: 100%; table-layout: fixed;">
    <colgroup>
        <col span="1" style="width: 10px;" />
        <col span="1" />
    </colgroup>
    <tbody>
        <tr>
            <td colspan="2">--rootfs string</td>
        </tr>
        <tr>
            <td></td>
            <td style="line-height: 130%; word-wrap: break-word;"><p>Шлях до реальної кореневої файлової системи хоста. Це призведе до зміни корення (chroot) kubeadm на вказаних шлях</p></td>
        </tr>
    </tbody>
</table>