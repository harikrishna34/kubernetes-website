
Вивід конфігурації

### Опис {#synopsis}

Ця команда виводить конфігурацію вказаних субкоманд. Докладніше: https://pkg.go.dev/k8s.io/kubernetes/cmd/kubeadm/app/apis/kubeadm#section-directories

```shell
kubeadm config print [flags]
```

### Параметри {#options}

<table style="width: 100%; table-layout: fixed;">
    <colgroup>
        <col span="1" style="width: 10px;" />
        <col span="1" />
    </colgroup>
    <tbody>
        <tr>
            <td colspan="2">-h, --help</td>
        </tr>
        <tr>
            <td></td>
            <td style="line-height: 130%; word-wrap: break-word;"><p>довідка print</p></td>
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
        <td colspan="2">--kubeconfig string&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Типово: "/etc/kubernetes/admin.conf"</td>
    </tr>
    <tr>
        <td></td>
        <td style="line-height: 130%; word-wrap: break-word;"><p>Файл kubeconfig для використання при спілкуванні з кластером. Якщо прапорець не встановлено, набір стандартних розташувань може бути перевірений на наявність поточного файлу kubeconfig.</p></td>
    </tr>
    <tr>
        <td colspan="2">--rootfs string</td>
    </tr>
    <tr>
        <td></td>
        <td style="line-height: 130%; word-wrap: break-word;"><p>Шлях до реальної кореневої файлової системи хоста. Це призведе до зміни корення (chroot) kubeadm на вказаних шлях</p></td>
    </tr>
    </tbody>
</table>