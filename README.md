# grimeb0y.github.io
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Grime Doom Calculator</title>
    <link rel="icon" type="image/png" href="https://prnt.sc/8xmbqpROmpza">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Roboto+Mono:wght@400;700&display=swap');
        @import url('https://fonts.googleapis.com/css2?family=MedievalSharp&display=swap');

        :root {
            --color-primary: #1e1e1e;
            --color-secondary: #2c2c2c;
            --color-accent: #3b3b3b;
            --color-text: #e0e0e0;
            --color-highlight: #ffcc00;
        }

        body {
            font-family: 'Roboto Mono', monospace;
            color: var(--color-text);
            background-image: url('https://i.ytimg.com/vi/YlwCmIcm0oM/hq720.jpg?sqp=-oaymwEhCK4FEIIDSFryq4qpAxMIARUAAAAAGAElAADIQj0AgKJD&rs=AOn4CLD8amUZ9KYXBSG5PAIzWKFBo-1Mag');
            background-size: cover;
            background-position: center;
            background-attachment: fixed;
            margin: 0;
            padding: 20px;
            display: flex;
            justify-content: center;
            align-items: flex-start;
            min-height: 100vh;
            text-shadow: 1px 1px 2px black;
        }

        .container {
            width: 100%;
            max-width: 900px;
            background-color: rgba(0, 0, 0, 0.75);
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
            border: 2px solid var(--color-accent);
        }

        h1 {
            font-family: 'MedievalSharp', cursive;
            text-align: center;
            font-size: 2.5em;
            color: var(--color-highlight);
            margin-bottom: 20px;
        }

        .section {
            background-color: var(--color-primary);
            padding: 20px;
            border-radius: 10px;
            margin-bottom: 20px;
            border: 1px solid var(--color-accent);
        }
        
        h2 {
            font-family: 'MedievalSharp', cursive;
            margin-top: 0;
            color: var(--color-highlight);
        }

        label {
            margin-bottom: 5px;
            font-weight: bold;
        }

        input[type="number"], input[type="text"] {
            background-color: var(--color-secondary);
            color: var(--color-text);
            border: 1px solid var(--color-accent);
            padding: 10px;
            border-radius: 5px;
            width: calc(100% - 22px);
            box-sizing: border-box;
        }
        
        .item-inputs, .wave-inputs-table {
            width: 100%;
            border-collapse: collapse;
            text-align: left;
        }
        
        .item-inputs td, .wave-inputs-table td {
            padding: 8px;
        }

        .item-inputs tr td:first-child {
            font-weight: bold;
        }
        
        .wave-inputs-table th {
            font-family: 'MedievalSharp', cursive;
            padding: 10px 8px;
            text-align: center;
            background-color: var(--color-accent);
        }

        .wave-inputs-table td {
            text-align: center;
            vertical-align: middle;
            border-top: 1px solid var(--color-accent);
        }
        
        .time-input-group {
            display: flex;
            gap: 5px;
        }

        .time-input-group input {
            flex: 1;
        }

        button {
            width: 100%;
            padding: 15px;
            background-color: var(--color-highlight);
            color: var(--color-primary);
            border: none;
            border-radius: 5px;
            font-size: 1.2em;
            font-weight: bold;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }

        button:hover {
            background-color: #ffda47;
        }
        
        #results {
            text-align: center;
        }
        
        #results p {
            font-size: 1.2em;
            margin: 10px 0;
        }
        
        #profit-total, #profit-per-hour {
            font-size: 1.5em;
            color: var(--color-highlight);
        }

    </style>
</head>
<body>

    <div class="container">
        <h1>Grime Doom Calculator</h1>

        <div class="section">
            <h2>Valores dos Itens</h2>
            <p>Altere os valores dos itens em GP (os valores iniciais são os do prompt).</p>
            <table class="item-inputs">
                <tr>
                    <td>Mokhaiotl cloth:</td>
                    <td><input type="number" id="price-cloth" value="98000000" min="0"></td>
                </tr>
                <tr>
                    <td>Eye of ayak:</td>
                    <td><input type="number" id="price-eye" value="70000000" min="0"></td>
                </tr>
                <tr>
                    <td>Avernic treads:</td>
                    <td><input type="number" id="price-treads" value="282000000" min="0"></td>
                </tr>
                <tr>
                    <td>Dom:</td>
                    <td><input type="number" id="price-dom" value="0" min="0"></td>
                </tr>
            </table>
        </div>
        
        <div class="section">
            <h2>Waves por Delve</h2>
            <p>Digite o número de waves e o tempo para cada nível de Delve.</p>
            <table class="wave-inputs-table">
                <thead>
                    <tr>
                        <th>Delve</th>
                        <th>Nº de Waves</th>
                        <th>Tempo (minutos/segundos)</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>1</td>
                        <td><input type="number" id="waves-1" value="0" min="0"></td>
                        <td><div class="time-input-group"><input type="number" id="time-1-min" value="0" min="0"><input type="number" id="time-1-sec" value="0" min="0" max="59"></div></td>
                    </tr>
                    <tr>
                        <td>2</td>
                        <td><input type="number" id="waves-2" value="0" min="0"></td>
                        <td><div class="time-input-group"><input type="number" id="time-2-min" value="0" min="0"><input type="number" id="time-2-sec" value="0" min="0" max="59"></div></td>
                    </tr>
                    <tr>
                        <td>3</td>
                        <td><input type="number" id="waves-3" value="0" min="0"></td>
                        <td><div class="time-input-group"><input type="number" id="time-3-min" value="0" min="0"><input type="number" id="time-3-sec" value="0" min="0" max="59"></div></td>
                    </tr>
                    <tr>
                        <td>4</td>
                        <td><input type="number" id="waves-4" value="0" min="0"></td>
                        <td><div class="time-input-group"><input type="number" id="time-4-min" value="0" min="0"><input type="number" id="time-4-sec" value="0" min="0" max="59"></div></td>
                    </tr>
                    <tr>
                        <td>5</td>
                        <td><input type="number" id="waves-5" value="0" min="0"></td>
                        <td><div class="time-input-group"><input type="number" id="time-5-min" value="0" min="0"><input type="number" id="time-5-sec" value="0" min="0" max="59"></div></td>
                    </tr>
                    <tr>
                        <td>6</td>
                        <td><input type="number" id="waves-6" value="0" min="0"></td>
                        <td><div class="time-input-group"><input type="number" id="time-6-min" value="0" min="0"><input type="number" id="time-6-sec" value="0" min="0" max="59"></div></td>
                    </tr>
                    <tr>
                        <td>7</td>
                        <td><input type="number" id="waves-7" value="0" min="0"></td>
                        <td><div class="time-input-group"><input type="number" id="time-7-min" value="0" min="0"><input type="number" id="time-7-sec" value="0" min="0" max="59"></div></td>
                    </tr>
                    <tr>
                        <td>8</td>
                        <td><input type="number" id="waves-8" value="0" min="0"></td>
                        <td><div class="time-input-group"><input type="number" id="time-8-min" value="0" min="0"><input type="number" id="time-8-sec" value="0" min="0" max="59"></div></td>
                    </tr>
                    <tr>
                        <td>9+</td>
                        <td><input type="number" id="waves-9plus" value="0" min="0"></td>
                        <td><div class="time-input-group"><input type="number" id="time-9plus-min" value="0" min="0"><input type="number" id="time-9plus-sec" value="0" min="0" max="59"></div></td>
                    </tr>
                </tbody>
            </table>
        </div>

        <button onclick="calculateProfit()">Calcular</button>

        <div class="section" id="results">
            <h2>Resultados</h2>
            <p>Lucro Total Esperado: <span id="profit-total">0 gp</span></p>
            <p>Lucro por Hora: <span id="profit-per-hour">0 gp/h</span></p>
        </div>
    </div>

    <script>
        // Taxas de drop individuais (1/chance) com base na imagem fornecida
        const dropRates = {
            cloth: { 2: 2500, 3: 2000, 4: 1350, 5: 810, 6: 765, 7: 720, 8: 630, '9+': 540 },
            eye: { 3: 2000, 4: 1350, 5: 810, 6: 765, 7: 720, 8: 630, '9+': 540 },
            treads: { 4: 1350, 5: 810, 6: 765, 7: 720, 8: 630, '9+': 540 },
            dom: { 6: 1000, 7: 750, 8: 500, '9+': 250 }
        };

        function calculateProfit() {
            // Pega os inputs dos preços dos itens
            const itemPrices = {
                cloth: parseInt(document.getElementById('price-cloth').value) || 0,
                eye: parseInt(document.getElementById('price-eye').value) || 0,
                treads: parseInt(document.getElementById('price-treads').value) || 0,
                dom: parseInt(document.getElementById('price-dom').value) || 0
            };

            let totalWaves = 0;
            let totalExpectedProfit = 0;
            let totalTimeInMinutes = 0;

            const delves = [1, 2, 3, 4, 5, 6, 7, 8, '9+'];

            for (const delve of delves) {
                const delveKey = delve.toString().replace('+', 'plus');
                
                // Pega o número de waves e o tempo para o delve atual
                const wavesAtDelve = parseInt(document.getElementById(`waves-${delveKey}`).value) || 0;
                const timeMinutes = parseInt(document.getElementById(`time-${delveKey}-min`).value) || 0;
                const timeSeconds = parseInt(document.getElementById(`time-${delveKey}-sec`).value) || 0;
                const timePerWave = timeMinutes + (timeSeconds / 60);

                totalWaves += wavesAtDelve;
                totalTimeInMinutes += wavesAtDelve * timePerWave;

                // Delve 1 não tem drops, então não calcula lucro
                if (delve === 1) {
                    continue;
                }

                // Calcula o lucro esperado para uma única wave (considerando apenas 1 item por wave)
                let expectedProfitForThisWave = 0;
                
                // Soma os valores esperados de cada item para uma wave.
                // Isso reflete a chance de cada item ser o drop em uma única wave.
                if (dropRates.cloth[delve]) {
                    expectedProfitForThisWave += (1 / dropRates.cloth[delve]) * itemPrices.cloth;
                }
                if (dropRates.eye[delve]) {
                    expectedProfitForThisWave += (1 / dropRates.eye[delve]) * itemPrices.eye;
                }
                if (dropRates.treads[delve]) {
                    expectedProfitForThisWave += (1 / dropRates.treads[delve]) * itemPrices.treads;
                }
                if (dropRates.dom[delve]) {
                    expectedProfitForThisWave += (1 / dropRates.dom[delve]) * itemPrices.dom;
                }

                // Adiciona o lucro total esperado para as waves deste delve
                totalExpectedProfit += wavesAtDelve * expectedProfitForThisWave;
            }

            // Exibe os resultados
            const totalProfitElement = document.getElementById('profit-total');
            const profitPerHourElement = document.getElementById('profit-per-hour');

            if (totalWaves === 0 || totalTimeInMinutes === 0) {
                totalProfitElement.textContent = '0 gp';
                profitPerHourElement.textContent = '0 gp/h';
                return;
            }
            
            // Formata os números para M (milhões) ou B (bilhões)
            const formatGp = (gp) => {
                if (gp >= 1000000000) {
                    return `${(gp / 1000000000).toFixed(2)} B`;
                }
                if (gp >= 1000000) {
                    return `${(gp / 1000000).toFixed(2)} M`;
                }
                return `${Math.round(gp).toLocaleString()} gp`;
            };

            const profitPerHour = (totalExpectedProfit / totalTimeInMinutes) * 60;

            totalProfitElement.textContent = formatGp(totalExpectedProfit);
            profitPerHourElement.textContent = formatGp(profitPerHour) + '/h';
        }
    </script>
</body>
</html>
