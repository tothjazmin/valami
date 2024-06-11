<!DOCTYPE html>

<html lang="hu" xmlns="http://www.w3.org/1999/xhtml">
<head>
    <meta charset="utf-8" />
    <title>Restponzív</title>

    <style>
        .container {
            text-align: center;
            margin-top: 50px;
        }

        .number-box {
            font-size: 3rem;
            margin-bottom: 20px;
        }

        .button {
            padding: 10px 20px;
            font-size: 1.2rem;
            margin: 0 10px;
            border: none;
            border-radius: 5px;
            background-color: #4CAF50;
            color: white;
            cursor: pointer;
        }

        .container {
      text-align: center;
      margin-top: 50px;
    }

    .column-box {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      grid-gap: 10px;
      margin-bottom: 20px;
    }

    .row {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      grid-gap: 10px;
    }

    .column {
      background-color: #ccc;
      padding: 20px;
      cursor: pointer;
    }

    .column.hidden {
      display: none;
    }

    .button {
      padding: 10px 20px;
      font-size: 1.2rem;
      border: none;
      border-radius: 5px;
      background-color: #4CAF50;
      color: white;
      cursor: pointer;
    }
        .list-item {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 10px;
            background-color: #f2f2f2;
            border-radius: 4px;
            margin-bottom: 5px;
        }

            .list-item span {
                flex: 1;
            }

            .list-item button {
                margin-left: 10px;
                padding: 5px 10px;
                font-size: 0.8rem;
                border: none;
                border-radius: 4px;
                background-color: #f44336;
                color: white;
                cursor: pointer;
            }
    </style>
</head>
<body>

    <div class="container">
        <div class="number-box" id="numberBox">0</div>
        <button class="button" onclick="changeNumber(1)">+</button>
        <button class="button" onclick="changeNumber(-1)">-</button>
    </div>
    <div class="container">
        <div class="column-box" id="columnBox">
            <div class="row">
                <div class="column"></div>
                <div class="column"></div>
                <div class="column"></div>
            </div>
            <div class="row">
                <div class="column"></div>
                <div class="column"></div>
                <div class="column"></div>
            </div>
            <div class="row">
                <div class="column"></div>
                <div class="column"></div>
                <div class="column"></div>
            </div>
        </div>
        <button class="button" onclick="resetColumns()">Újra</button>
    </div>

    <div class="container">
        <div class="input-container">
            <input type="text" id="listInput" placeholder="Írjon be egy listára felvenni kívánt adatot: ">
            <button onclick="addListItem()">Hozzáad</button>
        </div>
        <div id="listContainer"></div>
    </div>

    <script>
        let number = 0;
        const numberBox = document.getElementById('numberBox');

        function changeNumber(value) {
            number += value;
            numberBox.textContent = number;
        }

         const columnBox = document.getElementById('columnBox');
        const columns = columnBox.getElementsByClassName('column');

        for (let column of columns) {
            column.addEventListener('click', function () {
                this.classList.toggle('hidden');
            });
        }

        function resetColumns() {
            for (let column of columns) {
                column.classList.remove('hidden');
            }
        }
        const listInput = document.getElementById('listInput');
        const listContainer = document.getElementById('listContainer');

        function addListItem() {
            const itemText = listInput.value.trim();
            if (itemText !== '') {
                const listItem = document.createElement('div');
                listItem.classList.add('list-item');

                const itemSpan = document.createElement('span');
                itemSpan.textContent = itemText;
                listItem.append(itemSpan);

                const removeButton = document.createElement('button');
                removeButton.textContent = 'X';
                removeButton.addEventListener('click', function () {
                    listContainer.remove(listItem);
                });
                listItem.append(removeButton);

                listContainer.append(listItem);
                listInput.value = '';
            }
        }

    </script>


</body>
</html>
