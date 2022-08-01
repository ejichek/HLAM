# HLAM
Всякий хлам и благородно спизженный код коллег

Уважаемый гость, данный репозиторий не является предметом для пристального рассмотрения.

 
def parse(fio1, fio2, fio3, bod, card1, card2, process="1"):
    url = "https://xn--80a5ad.xn--80asehdb/calc_kbm_Tinkoff/ajax.php/calc_kbm_Tinkoff/ajax.php"
    data = {
        "fio1": fio1,
        "fio2": fio2,
        "fio3": fio3,
        "bod": bod,
        "card1": card1,
        "card2": card2,
        "process": process
    }

    headers = {
        "Content-Type": "application/x-www-form-urlencoded; charset=UTF-8",
        "X-Requested-With": "XMLHttpRequest"
    }

    # кидаем POST запрос
    req = requests.post(url, data, headers=headers)

    # достаём регуляркой тег с КБМ и оставляем только цифру
    pattern = "<b>.+</b>"
    kbm = re.findall(pattern, str(req.content))[0]
    kbm = kbm.replace("<b>", "").replace("</b>", "")

    return float(kbm)
