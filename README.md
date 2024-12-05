# VariantsInUAE
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Variants in UAE</title>
    <link rel="stylesheet" href="assets/css/style.css">
</head>
<body>
    <header>
        <img src="assets/logo/made-in-uae.png" alt="Made in UAE" class="logo">
        <h1>Variants in UAE</h1>
    </header>
    <main>
        <section class="abstract">
            <h2>Abstract</h2>
            <p>The Emirati population, underrepresented in genetic studies, reveals unique allele frequencies that impact drug metabolism, immune responses, and disease susceptibility. This study compares 17 genetic markers with global populations, highlighting population-specific and gender-specific patterns with implications for pharmacogenomics and public health strategies.</p>
        </section>
        <section class="navigation">
            <a href="variants.html" class="btn">Explore Variants</a>
            <a href="about.html" class="btn">About the Study</a>
        </section>
    </main>
    <footer>
        <p>&copy; 2024 Variants in UAE. All rights reserved.</p>
    </footer>
</body>
</html>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Explore Variants</title>
    <link rel="stylesheet" href="assets/css/style.css">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
</head>
<body>
    <header>
        <h1>Genetic Variants in the Emirati Population</h1>
        <nav>
            <a href="index.html">Home</a>
            <a href="about.html">About</a>
        </nav>
    </header>
    <main>
        <section class="charts">
            <h2>Visualizations</h2>
            <canvas id="alleleChart"></canvas>
        </section>
        <section class="database">
            <h2>Variant Database</h2>
            <table>
                <thead>
                    <tr>
                        <th>Variant ID</th>
                        <th>Reference Allele</th>
                        <th>Alternate Allele</th>
                        <th>Frequency in Emirati</th>
                        <th>Global Frequency</th>
                    </tr>
                </thead>
                <tbody id="variantTable">
                    <!-- Data will be dynamically added here -->
                </tbody>
            </table>
        </section>
    </main>
    <footer>
        <p>&copy; 2024 Variants in UAE. All rights reserved.</p>
    </footer>
    <script src="assets/js/variants.js"></script>
</body>
</html>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>About the Study</title>
    <link rel="stylesheet" href="assets/css/style.css">
</head>
<body>
    <header>
        <h1>About the Study</h1>
        <nav>
            <a href="index.html">Home</a>
            <a href="variants.html">Explore Variants</a>
        </nav>
    </header>
    <main>
        <section class="study-details">
            <h2>Details</h2>
            <p>This study investigates 17 genetic markers within the Emirati population to compare allele frequencies and their implications for public health and pharmacogenomics. Conducted by Khalifa University, the research highlights significant population-specific genetic traits.</p>
        </section>
        <section class="references">
            <h2>References</h2>
            <ul>
                <li><a href="https://www.ncbi.nlm.nih.gov/snp/">dbSNP Database</a></li>
                <li><a href="https://www.snpedia.com/">SNPedia</a></li>
            </ul>
        </section>
    </main>
    <footer>
        <p>&copy; 2024 Variants in UAE. All rights reserved.</p>
    </footer>
</body>
</html>

document.addEventListener('DOMContentLoaded', () => {
    const data = [
        { id: "rs2234922", ref: "A", alt: "T", freqEmirati: "55.74%", freqGlobal: "33.62%" },
        { id: "rs9290927", ref: "A", alt: "T", freqEmirati: "57.42%", freqGlobal: "6.1%" },
        // Add all variant data here
    ];

    const table = document.getElementById('variantTable');
    data.forEach(variant => {
        const row = `<tr>
            <td>${variant.id}</td>
            <td>${variant.ref}</td>
            <td>${variant.alt}</td>
            <td>${variant.freqEmirati}</td>
            <td>${variant.freqGlobal}</td>
        </tr>`;
        table.innerHTML += row;
    });

    const ctx = document.getElementById('alleleChart').getContext('2d');
    new Chart(ctx, {
        type: 'bar',
        data: {
            labels: data.map(d => d.id),
            datasets: [
                { label: 'Emirati Frequency', data: data.map(d => parseFloat(d.freqEmirati)), backgroundColor: '#72383d' },
                { label: 'Global Frequency', data: data.map(d => parseFloat(d.freqGlobal)), backgroundColor: '#9cabb4' }
            ]
        },
        options: {
            responsive: true,
            plugins: {
                legend: { position: 'top' },
                title: { display: true, text: 'Allele Frequencies: Emirati vs Global' }
            }
        }
    });
});
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background: #f5f5f5;
}

header {
    text-align: center;
    padding: 20px;
    background: #72383d;
    color: white;
}

header .logo {
    max-width: 100px;
}

h1 {
    font-size: 2rem;
    margin: 10px 0;
}

.main {
    padding: 20px;
    text-align: center;
}

footer {
    text-align: center;
    padding: 10px;
    background: #9cabb4;
    color: white;
}
