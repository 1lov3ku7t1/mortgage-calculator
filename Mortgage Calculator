<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Advanced Mortgage Calculator</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap');
        
        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(135deg, #f5f7fa 0%, #e4edf5 100%);
        }
        
        .slider {
            -webkit-appearance: none;
            height: 8px;
            border-radius: 5px;
            background: #d3d3d3;
            outline: none;
        }
        
        .slider::-webkit-slider-thumb {
            -webkit-appearance: none;
            appearance: none;
            width: 20px;
            height: 20px;
            border-radius: 50%;
            background: #3b82f6;
            cursor: pointer;
            transition: all 0.2s ease-in-out;
        }
        
        .slider::-webkit-slider-thumb:hover {
            background: #2563eb;
            transform: scale(1.1);
        }
        
        .tab-active {
            color: #3b82f6;
            border-bottom: 3px solid #3b82f6;
        }
        
        .chart-container {
            position: relative;
            height: 200px;
            width: 100%;
        }
        
        .amortization-row:nth-child(even) {
            background-color: rgba(59, 130, 246, 0.05);
        }
        
        @media (max-width: 768px) {
            .calculator-container {
                flex-direction: column;
            }
            
            .chart-container {
                height: 180px;
            }
        }
    </style>
</head>
<body class="min-h-screen p-4 md:p-8">
    <div class="max-w-6xl mx-auto bg-white rounded-xl shadow-lg overflow-hidden">
        <div class="bg-gradient-to-r from-blue-600 to-blue-800 p-6 text-white">
            <h1 class="text-2xl md:text-3xl font-bold">Advanced Mortgage Calculator</h1>
            <p class="mt-2 opacity-90">Calculate payments, compare scenarios, and plan your mortgage with precision</p>
        </div>
        
        <div class="p-6">
            <!-- Tabs -->
            <div class="flex border-b border-gray-200 mb-6">
                <button id="tab-calculator" class="px-4 py-2 font-medium text-sm tab-active">Calculator</button>
                <button id="tab-comparison" class="px-4 py-2 font-medium text-sm text-gray-500">Comparison</button>
                <button id="tab-amortization" class="px-4 py-2 font-medium text-sm text-gray-500">Amortization</button>
                <button id="tab-extra-payments" class="px-4 py-2 font-medium text-sm text-gray-500">Extra Payments</button>
            </div>
            
            <!-- Calculator Tab Content -->
            <div id="content-calculator" class="calculator-container flex flex-col md:flex-row gap-8">
                <div class="w-full md:w-1/2">
                    <div class="mb-6">
                        <label class="block text-sm font-medium text-gray-700 mb-1">Home Price</label>
                        <div class="flex items-center">
                            <span class="text-gray-500 mr-2">$</span>
                            <input type="number" id="home-price" class="w-full p-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500" value="300000">
                        </div>
                        <input type="range" id="home-price-slider" class="slider w-full mt-2" min="50000" max="2000000" step="5000" value="300000">
                        <div class="flex justify-between text-xs text-gray-500 mt-1">
                            <span>$50k</span>
                            <span>$2M</span>
                        </div>
                    </div>
                    
                    <div class="mb-6">
                        <label class="block text-sm font-medium text-gray-700 mb-1">Down Payment</label>
                        <div class="flex items-center gap-4">
                            <div class="flex items-center flex-1">
                                <span class="text-gray-500 mr-2">$</span>
                                <input type="number" id="down-payment" class="w-full p-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500" value="60000">
                            </div>
                            <div class="flex items-center w-24">
                                <input type="number" id="down-payment-percent" class="w-full p-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500" value="20">
                                <span class="text-gray-500 ml-2">%</span>
                            </div>
                        </div>
                        <input type="range" id="down-payment-slider" class="slider w-full mt-2" min="0" max="90" step="1" value="20">
                        <div class="flex justify-between text-xs text-gray-500 mt-1">
                            <span>0%</span>
                            <span>90%</span>
                        </div>
                    </div>
                    
                    <div class="mb-6">
                        <label class="block text-sm font-medium text-gray-700 mb-1">Loan Term</label>
                        <select id="loan-term" class="w-full p-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500">
                            <option value="30">30 years</option>
                            <option value="25">25 years</option>
                            <option value="20">20 years</option>
                            <option value="15">15 years</option>
                            <option value="10">10 years</option>
                        </select>
                    </div>
                    
                    <div class="mb-6">
                        <label class="block text-sm font-medium text-gray-700 mb-1">Interest Rate</label>
                        <div class="flex items-center">
                            <input type="number" id="interest-rate" class="w-full p-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500" value="4.5" step="0.01">
                            <span class="text-gray-500 ml-2">%</span>
                        </div>
                        <input type="range" id="interest-rate-slider" class="slider w-full mt-2" min="0.5" max="15" step="0.05" value="4.5">
                        <div class="flex justify-between text-xs text-gray-500 mt-1">
                            <span>0.5%</span>
                            <span>15%</span>
                        </div>
                    </div>
                    
                    <div class="mb-6">
                        <label class="block text-sm font-medium text-gray-700 mb-1">Property Tax (yearly)</label>
                        <div class="flex items-center">
                            <span class="text-gray-500 mr-2">$</span>
                            <input type="number" id="property-tax" class="w-full p-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500" value="3600">
                        </div>
                    </div>
                    
                    <div class="mb-6">
                        <label class="block text-sm font-medium text-gray-700 mb-1">Home Insurance (yearly)</label>
                        <div class="flex items-center">
                            <span class="text-gray-500 mr-2">$</span>
                            <input type="number" id="home-insurance" class="w-full p-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500" value="1200">
                        </div>
                    </div>
                    
                    <div class="mb-6">
                        <label class="block text-sm font-medium text-gray-700 mb-1">HOA Fees (monthly)</label>
                        <div class="flex items-center">
                            <span class="text-gray-500 mr-2">$</span>
                            <input type="number" id="hoa-fees" class="w-full p-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500" value="0">
                        </div>
                    </div>
                    
                    <div class="mb-6">
                        <label class="block text-sm font-medium text-gray-700 mb-1">PMI (Private Mortgage Insurance)</label>
                        <div class="flex items-center">
                            <input type="number" id="pmi-rate" class="w-full p-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500" value="0.5" step="0.01">
                            <span class="text-gray-500 ml-2">%</span>
                        </div>
                        <p class="text-xs text-gray-500 mt-1">Typically required if down payment is less than 20%</p>
                    </div>
                </div>
                
                <div class="w-full md:w-1/2">
                    <div class="bg-blue-50 p-6 rounded-lg mb-6">
                        <h2 class="text-xl font-semibold text-gray-800 mb-4">Monthly Payment Breakdown</h2>
                        <div class="flex justify-between mb-3">
                            <span class="text-gray-600">Principal & Interest:</span>
                            <span id="principal-interest" class="font-medium">$1,216.04</span>
                        </div>
                        <div class="flex justify-between mb-3">
                            <span class="text-gray-600">Property Tax:</span>
                            <span id="monthly-tax" class="font-medium">$300.00</span>
                        </div>
                        <div class="flex justify-between mb-3">
                            <span class="text-gray-600">Home Insurance:</span>
                            <span id="monthly-insurance" class="font-medium">$100.00</span>
                        </div>
                        <div class="flex justify-between mb-3">
                            <span class="text-gray-600">HOA Fees:</span>
                            <span id="monthly-hoa" class="font-medium">$0.00</span>
                        </div>
                        <div class="flex justify-between mb-3" id="pmi-row">
                            <span class="text-gray-600">PMI:</span>
                            <span id="monthly-pmi" class="font-medium">$0.00</span>
                        </div>
                        <div class="h-px bg-gray-300 my-3"></div>
                        <div class="flex justify-between text-lg font-bold">
                            <span>Total Monthly Payment:</span>
                            <span id="total-payment" class="text-blue-700">$1,616.04</span>
                        </div>
                    </div>
                    
                    <div class="bg-white border border-gray-200 rounded-lg p-6">
                        <h2 class="text-xl font-semibold text-gray-800 mb-4">Loan Summary</h2>
                        <div class="flex justify-between mb-3">
                            <span class="text-gray-600">Loan Amount:</span>
                            <span id="loan-amount" class="font-medium">$240,000.00</span>
                        </div>
                        <div class="flex justify-between mb-3">
                            <span class="text-gray-600">Total Interest Paid:</span>
                            <span id="total-interest" class="font-medium">$197,778.62</span>
                        </div>
                        <div class="flex justify-between mb-3">
                            <span class="text-gray-600">Total Cost of Loan:</span>
                            <span id="total-cost" class="font-medium">$437,778.62</span>
                        </div>
                        <div class="flex justify-between mb-3">
                            <span class="text-gray-600">Loan Payoff Date:</span>
                            <span id="payoff-date" class="font-medium">May 2053</span>
                        </div>
                    </div>
                    
                    <div class="mt-6">
                        <h2 class="text-xl font-semibold text-gray-800 mb-4">Payment Distribution</h2>
                        <div class="chart-container">
                            <canvas id="payment-chart"></canvas>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Comparison Tab Content -->
            <div id="content-comparison" class="hidden">
                <div class="flex flex-col md:flex-row gap-6 mb-6">
                    <div class="w-full md:w-1/2 p-4 border border-gray-200 rounded-lg">
                        <h3 class="text-lg font-medium mb-4">Scenario 1</h3>
                        <div class="grid grid-cols-2 gap-4">
                            <div>
                                <label class="block text-sm font-medium text-gray-700 mb-1">Home Price</label>
                                <div class="flex items-center">
                                    <span class="text-gray-500 mr-2">$</span>
                                    <input type="number" id="comp1-price" class="w-full p-2 border border-gray-300 rounded-md" value="300000">
                                </div>
                            </div>
                            <div>
                                <label class="block text-sm font-medium text-gray-700 mb-1">Down Payment %</label>
                                <div class="flex items-center">
                                    <input type="number" id="comp1-down" class="w-full p-2 border border-gray-300 rounded-md" value="20">
                                    <span class="text-gray-500 ml-2">%</span>
                                </div>
                            </div>
                            <div>
                                <label class="block text-sm font-medium text-gray-700 mb-1">Term (years)</label>
                                <select id="comp1-term" class="w-full p-2 border border-gray-300 rounded-md">
                                    <option value="30">30 years</option>
                                    <option value="15">15 years</option>
                                </select>
                            </div>
                            <div>
                                <label class="block text-sm font-medium text-gray-700 mb-1">Interest Rate</label>
                                <div class="flex items-center">
                                    <input type="number" id="comp1-rate" class="w-full p-2 border border-gray-300 rounded-md" value="4.5" step="0.01">
                                    <span class="text-gray-500 ml-2">%</span>
                                </div>
                            </div>
                        </div>
                        <div class="mt-4 p-3 bg-blue-50 rounded-md">
                            <div class="flex justify-between mb-2">
                                <span class="text-gray-600">Monthly Payment:</span>
                                <span id="comp1-payment" class="font-medium">$1,216.04</span>
                            </div>
                            <div class="flex justify-between">
                                <span class="text-gray-600">Total Interest:</span>
                                <span id="comp1-interest" class="font-medium">$197,778.62</span>
                            </div>
                        </div>
                    </div>
                    
                    <div class="w-full md:w-1/2 p-4 border border-gray-200 rounded-lg">
                        <h3 class="text-lg font-medium mb-4">Scenario 2</h3>
                        <div class="grid grid-cols-2 gap-4">
                            <div>
                                <label class="block text-sm font-medium text-gray-700 mb-1">Home Price</label>
                                <div class="flex items-center">
                                    <span class="text-gray-500 mr-2">$</span>
                                    <input type="number" id="comp2-price" class="w-full p-2 border border-gray-300 rounded-md" value="300000">
                                </div>
                            </div>
                            <div>
                                <label class="block text-sm font-medium text-gray-700 mb-1">Down Payment %</label>
                                <div class="flex items-center">
                                    <input type="number" id="comp2-down" class="w-full p-2 border border-gray-300 rounded-md" value="20">
                                    <span class="text-gray-500 ml-2">%</span>
                                </div>
                            </div>
                            <div>
                                <label class="block text-sm font-medium text-gray-700 mb-1">Term (years)</label>
                                <select id="comp2-term" class="w-full p-2 border border-gray-300 rounded-md">
                                    <option value="30">30 years</option>
                                    <option value="15" selected>15 years</option>
                                </select>
                            </div>
                            <div>
                                <label class="block text-sm font-medium text-gray-700 mb-1">Interest Rate</label>
                                <div class="flex items-center">
                                    <input type="number" id="comp2-rate" class="w-full p-2 border border-gray-300 rounded-md" value="4.0" step="0.01">
                                    <span class="text-gray-500 ml-2">%</span>
                                </div>
                            </div>
                        </div>
                        <div class="mt-4 p-3 bg-blue-50 rounded-md">
                            <div class="flex justify-between mb-2">
                                <span class="text-gray-600">Monthly Payment:</span>
                                <span id="comp2-payment" class="font-medium">$1,775.25</span>
                            </div>
                            <div class="flex justify-between">
                                <span class="text-gray-600">Total Interest:</span>
                                <span id="comp2-interest" class="font-medium">$79,544.80</span>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="bg-white border border-gray-200 rounded-lg p-6">
                    <h2 class="text-xl font-semibold text-gray-800 mb-4">Comparison Results</h2>
                    <div class="overflow-x-auto">
                        <table class="w-full text-sm">
                            <thead>
                                <tr class="bg-gray-100">
                                    <th class="p-3 text-left">Metric</th>
                                    <th class="p-3 text-right">Scenario 1</th>
                                    <th class="p-3 text-right">Scenario 2</th>
                                    <th class="p-3 text-right">Difference</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr class="border-b border-gray-200">
                                    <td class="p-3">Monthly Payment</td>
                                    <td class="p-3 text-right" id="comp-table-payment1">$1,216.04</td>
                                    <td class="p-3 text-right" id="comp-table-payment2">$1,775.25</td>
                                    <td class="p-3 text-right font-medium text-red-600" id="comp-table-payment-diff">+$559.21</td>
                                </tr>
                                <tr class="border-b border-gray-200">
                                    <td class="p-3">Total Interest</td>
                                    <td class="p-3 text-right" id="comp-table-interest1">$197,778.62</td>
                                    <td class="p-3 text-right" id="comp-table-interest2">$79,544.80</td>
                                    <td class="p-3 text-right font-medium text-green-600" id="comp-table-interest-diff">-$118,233.82</td>
                                </tr>
                                <tr class="border-b border-gray-200">
                                    <td class="p-3">Total Cost</td>
                                    <td class="p-3 text-right" id="comp-table-cost1">$437,778.62</td>
                                    <td class="p-3 text-right" id="comp-table-cost2">$319,544.80</td>
                                    <td class="p-3 text-right font-medium text-green-600" id="comp-table-cost-diff">-$118,233.82</td>
                                </tr>
                                <tr>
                                    <td class="p-3">Payoff Timeline</td>
                                    <td class="p-3 text-right" id="comp-table-time1">30 years</td>
                                    <td class="p-3 text-right" id="comp-table-time2">15 years</td>
                                    <td class="p-3 text-right font-medium text-green-600" id="comp-table-time-diff">15 years sooner</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                    
                    <div class="mt-6">
                        <h3 class="text-lg font-medium mb-3">Interest Paid Over Time</h3>
                        <div class="chart-container">
                            <canvas id="comparison-chart"></canvas>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Amortization Tab Content -->
            <div id="content-amortization" class="hidden">
                <div class="mb-6 flex flex-col md:flex-row gap-4 items-end">
                    <div>
                        <label class="block text-sm font-medium text-gray-700 mb-1">Show</label>
                        <select id="amortization-view" class="w-full p-2 border border-gray-300 rounded-md">
                            <option value="yearly">Yearly Summary</option>
                            <option value="monthly">Monthly Details</option>
                        </select>
                    </div>
                    <div>
                        <label class="block text-sm font-medium text-gray-700 mb-1">Display Years</label>
                        <select id="amortization-years" class="w-full p-2 border border-gray-300 rounded-md">
                            <option value="all">All Years</option>
                            <option value="5">First 5 Years</option>
                            <option value="10">First 10 Years</option>
                        </select>
                    </div>
                    <button id="export-amortization" class="bg-blue-600 hover:bg-blue-700 text-white py-2 px-4 rounded-md transition-colors">
                        Export Schedule
                    </button>
                </div>
                
                <div class="bg-white border border-gray-200 rounded-lg overflow-hidden">
                    <div class="p-4 bg-gray-50 border-b border-gray-200">
                        <h2 class="text-xl font-semibold text-gray-800">Amortization Schedule</h2>
                    </div>
                    <div class="overflow-x-auto">
                        <table class="w-full text-sm">
                            <thead>
                                <tr class="bg-gray-100">
                                    <th class="p-3 text-left">Period</th>
                                    <th class="p-3 text-right">Payment</th>
                                    <th class="p-3 text-right">Principal</th>
                                    <th class="p-3 text-right">Interest</th>
                                    <th class="p-3 text-right">Total Interest</th>
                                    <th class="p-3 text-right">Balance</th>
                                </tr>
                            </thead>
                            <tbody id="amortization-table">
                                <!-- Amortization data will be inserted here -->
                            </tbody>
                        </table>
                    </div>
                </div>
                
                <div class="mt-6">
                    <h3 class="text-lg font-medium mb-3">Principal vs Interest Over Time</h3>
                    <div class="chart-container h-64">
                        <canvas id="amortization-chart"></canvas>
                    </div>
                </div>
            </div>
            
            <!-- Extra Payments Tab Content -->
            <div id="content-extra-payments" class="hidden">
                <div class="flex flex-col md:flex-row gap-8">
                    <div class="w-full md:w-1/2">
                        <div class="mb-6">
                            <h2 class="text-xl font-semibold text-gray-800 mb-4">Extra Payment Options</h2>
                            
                            <div class="mb-4">
                                <label class="block text-sm font-medium text-gray-700 mb-1">Extra Monthly Payment</label>
                                <div class="flex items-center">
                                    <span class="text-gray-500 mr-2">$</span>
                                    <input type="number" id="extra-monthly" class="w-full p-2 border border-gray-300 rounded-md" value="0">
                                </div>
                            </div>
                            
                            <div class="mb-4">
                                <label class="block text-sm font-medium text-gray-700 mb-1">Annual Lump Sum Payment</label>
                                <div class="flex items-center">
                                    <span class="text-gray-500 mr-2">$</span>
                                    <input type="number" id="extra-annual" class="w-full p-2 border border-gray-300 rounded-md" value="0">
                                </div>
                            </div>
                            
                            <div class="mb-4">
                                <label class="block text-sm font-medium text-gray-700 mb-1">One-time Payment</label>
                                <div class="flex items-center gap-4">
                                    <div class="flex items-center flex-1">
                                        <span class="text-gray-500 mr-2">$</span>
                                        <input type="number" id="extra-onetime-amount" class="w-full p-2 border border-gray-300 rounded-md" value="0">
                                    </div>
                                    <div class="flex items-center w-32">
                                        <span class="text-gray-500 mr-2">Month:</span>
                                        <input type="number" id="extra-onetime-month" class="w-full p-2 border border-gray-300 rounded-md" value="12" min="1">
                                    </div>
                                </div>
                            </div>
                            
                            <button id="calculate-extra" class="mt-2 bg-blue-600 hover:bg-blue-700 text-white py-2 px-4 rounded-md transition-colors">
                                Calculate Impact
                            </button>
                        </div>
                        
                        <div class="bg-blue-50 p-6 rounded-lg">
                            <h3 class="text-lg font-medium mb-3">Extra Payment Impact</h3>
                            
                            <div class="flex justify-between mb-3">
                                <span class="text-gray-600">Loan Payoff Time:</span>
                                <div>
                                    <span id="original-term" class="font-medium">30 years</span>
                                    <span class="mx-2">→</span>
                                    <span id="new-term" class="font-medium text-green-600">27 years 3 months</span>
                                </div>
                            </div>
                            
                            <div class="flex justify-between mb-3">
                                <span class="text-gray-600">Time Saved:</span>
                                <span id="time-saved" class="font-medium text-green-600">2 years 9 months</span>
                            </div>
                            
                            <div class="flex justify-between mb-3">
                                <span class="text-gray-600">Interest Savings:</span>
                                <span id="interest-saved" class="font-medium text-green-600">$28,123.45</span>
                            </div>
                            
                            <div class="flex justify-between">
                                <span class="text-gray-600">Total Extra Payments:</span>
                                <span id="total-extra" class="font-medium">$12,000.00</span>
                            </div>
                        </div>
                    </div>
                    
                    <div class="w-full md:w-1/2">
                        <h3 class="text-lg font-medium mb-3">Payment Comparison</h3>
                        <div class="chart-container h-64 mb-6">
                            <canvas id="extra-payment-chart"></canvas>
                        </div>
                        
                        <h3 class="text-lg font-medium mb-3">Balance Reduction</h3>
                        <div class="chart-container h-64">
                            <canvas id="balance-reduction-chart"></canvas>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <script>
        // Initialize variables
        let homePrice = 300000;
        let downPayment = 60000;
        let downPaymentPercent = 20;
        let loanTerm = 30;
        let interestRate = 4.5;
        let propertyTax = 3600;
        let homeInsurance = 1200;
        let hoaFees = 0;
        let pmiRate = 0.5;
        
        // DOM elements
        const homePriceInput = document.getElementById('home-price');
        const homePriceSlider = document.getElementById('home-price-slider');
        const downPaymentInput = document.getElementById('down-payment');
        const downPaymentPercentInput = document.getElementById('down-payment-percent');
        const downPaymentSlider = document.getElementById('down-payment-slider');
        const loanTermSelect = document.getElementById('loan-term');
        const interestRateInput = document.getElementById('interest-rate');
        const interestRateSlider = document.getElementById('interest-rate-slider');
        const propertyTaxInput = document.getElementById('property-tax');
        const homeInsuranceInput = document.getElementById('home-insurance');
        const hoaFeesInput = document.getElementById('hoa-fees');
        const pmiRateInput = document.getElementById('pmi-rate');
        
        // Result elements
        const principalInterestElement = document.getElementById('principal-interest');
        const monthlyTaxElement = document.getElementById('monthly-tax');
        const monthlyInsuranceElement = document.getElementById('monthly-insurance');
        const monthlyHoaElement = document.getElementById('monthly-hoa');
        const monthlyPmiElement = document.getElementById('monthly-pmi');
        const totalPaymentElement = document.getElementById('total-payment');
        const loanAmountElement = document.getElementById('loan-amount');
        const totalInterestElement = document.getElementById('total-interest');
        const totalCostElement = document.getElementById('total-cost');
        const payoffDateElement = document.getElementById('payoff-date');
        const pmiRowElement = document.getElementById('pmi-row');
        
        // Tab elements
        const tabCalculator = document.getElementById('tab-calculator');
        const tabComparison = document.getElementById('tab-comparison');
        const tabAmortization = document.getElementById('tab-amortization');
        const tabExtraPayments = document.getElementById('tab-extra-payments');
        
        const contentCalculator = document.getElementById('content-calculator');
        const contentComparison = document.getElementById('content-comparison');
        const contentAmortization = document.getElementById('content-amortization');
        const contentExtraPayments = document.getElementById('content-extra-payments');
        
        // Charts
        let paymentChart;
        let comparisonChart;
        let amortizationChart;
        let extraPaymentChart;
        let balanceReductionChart;
        
        // Initialize the calculator
        function initCalculator() {
            // Set up event listeners
            homePriceInput.addEventListener('input', updateFromHomePrice);
            homePriceSlider.addEventListener('input', updateFromHomePriceSlider);
            downPaymentInput.addEventListener('input', updateFromDownPayment);
            downPaymentPercentInput.addEventListener('input', updateFromDownPaymentPercent);
            downPaymentSlider.addEventListener('input', updateFromDownPaymentSlider);
            loanTermSelect.addEventListener('change', calculate);
            interestRateInput.addEventListener('input', updateFromInterestRate);
            interestRateSlider.addEventListener('input', updateFromInterestRateSlider);
            propertyTaxInput.addEventListener('input', calculate);
            homeInsuranceInput.addEventListener('input', calculate);
            hoaFeesInput.addEventListener('input', calculate);
            pmiRateInput.addEventListener('input', calculate);
            
            // Tab event listeners
            tabCalculator.addEventListener('click', () => switchTab('calculator'));
            tabComparison.addEventListener('click', () => switchTab('comparison'));
            tabAmortization.addEventListener('click', () => switchTab('amortization'));
            tabExtraPayments.addEventListener('click', () => switchTab('extra-payments'));
            
            // Comparison tab event listeners
            document.getElementById('comp1-price').addEventListener('input', updateComparison);
            document.getElementById('comp1-down').addEventListener('input', updateComparison);
            document.getElementById('comp1-term').addEventListener('change', updateComparison);
            document.getElementById('comp1-rate').addEventListener('input', updateComparison);
            document.getElementById('comp2-price').addEventListener('input', updateComparison);
            document.getElementById('comp2-down').addEventListener('input', updateComparison);
            document.getElementById('comp2-term').addEventListener('change', updateComparison);
            document.getElementById('comp2-rate').addEventListener('input', updateComparison);
            
            // Amortization tab event listeners
            document.getElementById('amortization-view').addEventListener('change', updateAmortizationTable);
            document.getElementById('amortization-years').addEventListener('change', updateAmortizationTable);
            document.getElementById('export-amortization').addEventListener('click', exportAmortizationSchedule);
            
            // Extra payments tab event listeners
            document.getElementById('calculate-extra').addEventListener('click', calculateExtraPayments);
            
            // Initial calculation
            calculate();
        }
        
        // Switch between tabs
        function switchTab(tab) {
            // Remove active class from all tabs
            tabCalculator.classList.remove('tab-active');
            tabComparison.classList.remove('tab-active');
            tabAmortization.classList.remove('tab-active');
            tabExtraPayments.classList.remove('tab-active');
            
            tabCalculator.classList.add('text-gray-500');
            tabComparison.classList.add('text-gray-500');
            tabAmortization.classList.add('text-gray-500');
            tabExtraPayments.classList.add('text-gray-500');
            
            // Hide all content
            contentCalculator.classList.add('hidden');
            contentComparison.classList.add('hidden');
            contentAmortization.classList.add('hidden');
            contentExtraPayments.classList.add('hidden');
            
            // Show selected tab and content
            if (tab === 'calculator') {
                tabCalculator.classList.add('tab-active');
                tabCalculator.classList.remove('text-gray-500');
                contentCalculator.classList.remove('hidden');
                initPaymentChart();
            } else if (tab === 'comparison') {
                tabComparison.classList.add('tab-active');
                tabComparison.classList.remove('text-gray-500');
                contentComparison.classList.remove('hidden');
                updateComparison();
            } else if (tab === 'amortization') {
                tabAmortization.classList.add('tab-active');
                tabAmortization.classList.remove('text-gray-500');
                contentAmortization.classList.remove('hidden');
                updateAmortizationTable();
                initAmortizationChart();
            } else if (tab === 'extra-payments') {
                tabExtraPayments.classList.add('tab-active');
                tabExtraPayments.classList.remove('text-gray-500');
                contentExtraPayments.classList.remove('hidden');
                calculateExtraPayments();
            }
        }
        
        // Update values when home price input changes
        function updateFromHomePrice() {
            homePrice = parseFloat(homePriceInput.value) || 0;
            homePriceSlider.value = homePrice;
            
            // Update down payment amount based on percentage
            downPayment = Math.round(homePrice * (downPaymentPercent / 100));
            downPaymentInput.value = downPayment;
            
            calculate();
        }
        
        // Update values when home price slider changes
        function updateFromHomePriceSlider() {
            homePrice = parseFloat(homePriceSlider.value);
            homePriceInput.value = homePrice;
            
            // Update down payment amount based on percentage
            downPayment = Math.round(homePrice * (downPaymentPercent / 100));
            downPaymentInput.value = downPayment;
            
            calculate();
        }
        
        // Update values when down payment input changes
        function updateFromDownPayment() {
            downPayment = parseFloat(downPaymentInput.value) || 0;
            
            // Update down payment percentage
            downPaymentPercent = Math.round((downPayment / homePrice) * 100);
            downPaymentPercentInput.value = downPaymentPercent;
            downPaymentSlider.value = downPaymentPercent;
            
            calculate();
        }
        
        // Update values when down payment percentage input changes
        function updateFromDownPaymentPercent() {
            downPaymentPercent = parseFloat(downPaymentPercentInput.value) || 0;
            
            // Limit to 0-100%
            if (downPaymentPercent > 100) downPaymentPercent = 100;
            if (downPaymentPercent < 0) downPaymentPercent = 0;
            
            downPaymentPercentInput.value = downPaymentPercent;
            downPaymentSlider.value = downPaymentPercent;
            
            // Update down payment amount
            downPayment = Math.round(homePrice * (downPaymentPercent / 100));
            downPaymentInput.value = downPayment;
            
            calculate();
        }
        
        // Update values when down payment slider changes
        function updateFromDownPaymentSlider() {
            downPaymentPercent = parseFloat(downPaymentSlider.value);
            downPaymentPercentInput.value = downPaymentPercent;
            
            // Update down payment amount
            downPayment = Math.round(homePrice * (downPaymentPercent / 100));
            downPaymentInput.value = downPayment;
            
            calculate();
        }
        
        // Update values when interest rate input changes
        function updateFromInterestRate() {
            interestRate = parseFloat(interestRateInput.value) || 0;
            interestRateSlider.value = interestRate;
            calculate();
        }
        
        // Update values when interest rate slider changes
        function updateFromInterestRateSlider() {
            interestRate = parseFloat(interestRateSlider.value);
            interestRateInput.value = interestRate;
            calculate();
        }
        
        // Calculate mortgage payments and update the UI
        function calculate() {
            // Get values from inputs
            loanTerm = parseInt(loanTermSelect.value);
            propertyTax = parseFloat(propertyTaxInput.value) || 0;
            homeInsurance = parseFloat(homeInsuranceInput.value) || 0;
            hoaFees = parseFloat(hoaFeesInput.value) || 0;
            pmiRate = parseFloat(pmiRateInput.value) || 0;
            
            // Calculate loan amount
            const loanAmount = homePrice - downPayment;
            
            // Calculate monthly interest rate
            const monthlyRate = interestRate / 100 / 12;
            
            // Calculate number of payments
            const numberOfPayments = loanTerm * 12;
            
            // Calculate principal and interest payment
            let monthlyPrincipalInterest = 0;
            if (monthlyRate > 0) {
                monthlyPrincipalInterest = loanAmount * monthlyRate * Math.pow(1 + monthlyRate, numberOfPayments) / (Math.pow(1 + monthlyRate, numberOfPayments) - 1);
            } else {
                monthlyPrincipalInterest = loanAmount / numberOfPayments;
            }
            
            // Calculate monthly property tax and insurance
            const monthlyTax = propertyTax / 12;
            const monthlyInsurance = homeInsurance / 12;
            
            // Calculate PMI if down payment is less than 20%
            let monthlyPmi = 0;
            if (downPaymentPercent < 20) {
                monthlyPmi = (loanAmount * (pmiRate / 100)) / 12;
                pmiRowElement.style.display = 'flex';
            } else {
                pmiRowElement.style.display = 'none';
            }
            
            // Calculate total monthly payment
            const totalMonthlyPayment = monthlyPrincipalInterest + monthlyTax + monthlyInsurance + hoaFees + monthlyPmi;
            
            // Calculate total interest paid
            const totalInterest = (monthlyPrincipalInterest * numberOfPayments) - loanAmount;
            
            // Calculate total cost of loan
            const totalCost = loanAmount + totalInterest;
            
            // Calculate payoff date
            const today = new Date();
            const payoffDate = new Date(today);
            payoffDate.setFullYear(today.getFullYear() + loanTerm);
            const payoffMonth = payoffDate.toLocaleString('default', { month: 'long' });
            const payoffYear = payoffDate.getFullYear();
            
            // Update UI with calculated values
            principalInterestElement.textContent = formatCurrency(monthlyPrincipalInterest);
            monthlyTaxElement.textContent = formatCurrency(monthlyTax);
            monthlyInsuranceElement.textContent = formatCurrency(monthlyInsurance);
            monthlyHoaElement.textContent = formatCurrency(hoaFees);
            monthlyPmiElement.textContent = formatCurrency(monthlyPmi);
            totalPaymentElement.textContent = formatCurrency(totalMonthlyPayment);
            loanAmountElement.textContent = formatCurrency(loanAmount);
            totalInterestElement.textContent = formatCurrency(totalInterest);
            totalCostElement.textContent = formatCurrency(totalCost);
            payoffDateElement.textContent = `${payoffMonth} ${payoffYear}`;
            
            // Update payment chart
            if (paymentChart) {
                updatePaymentChart(monthlyPrincipalInterest, monthlyTax, monthlyInsurance, hoaFees, monthlyPmi);
            }
        }
        
        // Initialize the payment breakdown chart
        function initPaymentChart() {
            const ctx = document.getElementById('payment-chart').getContext('2d');
            
            // Get values for chart
            const principalInterest = parseFloat(principalInterestElement.textContent.replace(/[^0-9.-]+/g, ''));
            const tax = parseFloat(monthlyTaxElement.textContent.replace(/[^0-9.-]+/g, ''));
            const insurance = parseFloat(monthlyInsuranceElement.textContent.replace(/[^0-9.-]+/g, ''));
            const hoa = parseFloat(monthlyHoaElement.textContent.replace(/[^0-9.-]+/g, ''));
            const pmi = parseFloat(monthlyPmiElement.textContent.replace(/[^0-9.-]+/g, ''));
            
            // Destroy existing chart if it exists
            if (paymentChart) {
                paymentChart.destroy();
            }
            
            // Create new chart
            paymentChart = new Chart(ctx, {
                type: 'doughnut',
                data: {
                    labels: ['Principal & Interest', 'Property Tax', 'Home Insurance', 'HOA Fees', 'PMI'],
                    datasets: [{
                        data: [principalInterest, tax, insurance, hoa, pmi],
                        backgroundColor: [
                            '#3b82f6',
                            '#10b981',
                            '#f59e0b',
                            '#6366f1',
                            '#ef4444'
                        ],
                        borderWidth: 1
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            position: 'bottom'
                        }
                    }
                }
            });
        }
        
        // Update the payment chart with new values
        function updatePaymentChart(principalInterest, tax, insurance, hoa, pmi) {
            if (paymentChart) {
                paymentChart.data.datasets[0].data = [principalInterest, tax, insurance, hoa, pmi];
                paymentChart.update();
            }
        }
        
        // Update comparison tab calculations
        function updateComparison() {
            // Get values from inputs
            const comp1Price = parseFloat(document.getElementById('comp1-price').value) || 0;
            const comp1Down = parseFloat(document.getElementById('comp1-down').value) || 0;
            const comp1Term = parseInt(document.getElementById('comp1-term').value);
            const comp1Rate = parseFloat(document.getElementById('comp1-rate').value) || 0;
            
            const comp2Price = parseFloat(document.getElementById('comp2-price').value) || 0;
            const comp2Down = parseFloat(document.getElementById('comp2-down').value) || 0;
            const comp2Term = parseInt(document.getElementById('comp2-term').value);
            const comp2Rate = parseFloat(document.getElementById('comp2-rate').value) || 0;
            
            // Calculate loan amounts
            const comp1LoanAmount = comp1Price * (1 - comp1Down / 100);
            const comp2LoanAmount = comp2Price * (1 - comp2Down / 100);
            
            // Calculate monthly rates
            const comp1MonthlyRate = comp1Rate / 100 / 12;
            const comp2MonthlyRate = comp2Rate / 100 / 12;
            
            // Calculate number of payments
            const comp1Payments = comp1Term * 12;
            const comp2Payments = comp2Term * 12;
            
            // Calculate monthly payments
            let comp1Payment = 0;
            if (comp1MonthlyRate > 0) {
                comp1Payment = comp1LoanAmount * comp1MonthlyRate * Math.pow(1 + comp1MonthlyRate, comp1Payments) / (Math.pow(1 + comp1MonthlyRate, comp1Payments) - 1);
            } else {
                comp1Payment = comp1LoanAmount / comp1Payments;
            }
            
            let comp2Payment = 0;
            if (comp2MonthlyRate > 0) {
                comp2Payment = comp2LoanAmount * comp2MonthlyRate * Math.pow(1 + comp2MonthlyRate, comp2Payments) / (Math.pow(1 + comp2MonthlyRate, comp2Payments) - 1);
            } else {
                comp2Payment = comp2LoanAmount / comp2Payments;
            }
            
            // Calculate total interest
            const comp1Interest = (comp1Payment * comp1Payments) - comp1LoanAmount;
            const comp2Interest = (comp2Payment * comp2Payments) - comp2LoanAmount;
            
            // Calculate total costs
            const comp1Cost = comp1LoanAmount + comp1Interest;
            const comp2Cost = comp2LoanAmount + comp2Interest;
            
            // Update UI
            document.getElementById('comp1-payment').textContent = formatCurrency(comp1Payment);
            document.getElementById('comp1-interest').textContent = formatCurrency(comp1Interest);
            document.getElementById('comp2-payment').textContent = formatCurrency(comp2Payment);
            document.getElementById('comp2-interest').textContent = formatCurrency(comp2Interest);
            
            document.getElementById('comp-table-payment1').textContent = formatCurrency(comp1Payment);
            document.getElementById('comp-table-payment2').textContent = formatCurrency(comp2Payment);
            document.getElementById('comp-table-interest1').textContent = formatCurrency(comp1Interest);
            document.getElementById('comp-table-interest2').textContent = formatCurrency(comp2Interest);
            document.getElementById('comp-table-cost1').textContent = formatCurrency(comp1Cost);
            document.getElementById('comp-table-cost2').textContent = formatCurrency(comp2Cost);
            document.getElementById('comp-table-time1').textContent = `${comp1Term} years`;
            document.getElementById('comp-table-time2').textContent = `${comp2Term} years`;
            
            // Calculate differences
            const paymentDiff = comp2Payment - comp1Payment;
            const interestDiff = comp2Interest - comp1Interest;
            const costDiff = comp2Cost - comp1Cost;
            const timeDiff = comp2Term - comp1Term;
            
            // Update difference columns
            document.getElementById('comp-table-payment-diff').textContent = formatCurrency(paymentDiff, true);
            document.getElementById('comp-table-payment-diff').className = paymentDiff > 0 ? 'p-3 text-right font-medium text-red-600' : 'p-3 text-right font-medium text-green-600';
            
            document.getElementById('comp-table-interest-diff').textContent = formatCurrency(interestDiff, true);
            document.getElementById('comp-table-interest-diff').className = interestDiff > 0 ? 'p-3 text-right font-medium text-red-600' : 'p-3 text-right font-medium text-green-600';
            
            document.getElementById('comp-table-cost-diff').textContent = formatCurrency(costDiff, true);
            document.getElementById('comp-table-cost-diff').className = costDiff > 0 ? 'p-3 text-right font-medium text-red-600' : 'p-3 text-right font-medium text-green-600';
            
            if (timeDiff === 0) {
                document.getElementById('comp-table-time-diff').textContent = 'Same';
                document.getElementById('comp-table-time-diff').className = 'p-3 text-right font-medium text-gray-600';
            } else if (timeDiff > 0) {
                document.getElementById('comp-table-time-diff').textContent = `${Math.abs(timeDiff)} years longer`;
                document.getElementById('comp-table-time-diff').className = 'p-3 text-right font-medium text-red-600';
            } else {
                document.getElementById('comp-table-time-diff').textContent = `${Math.abs(timeDiff)} years sooner`;
                document.getElementById('comp-table-time-diff').className = 'p-3 text-right font-medium text-green-600';
            }
            
            // Update comparison chart
            initComparisonChart(comp1Term, comp2Term, comp1Interest, comp2Interest);
        }
        
        // Initialize the comparison chart
        function initComparisonChart(term1, term2, interest1, interest2) {
            const ctx = document.getElementById('comparison-chart').getContext('2d');
            
            // Destroy existing chart if it exists
            if (comparisonChart) {
                comparisonChart.destroy();
            }
            
            // Generate data points for interest paid over time
            const maxTerm = Math.max(term1, term2);
            const labels = Array.from({length: maxTerm}, (_, i) => `Year ${i + 1}`);
            
            // Calculate interest paid per year for scenario 1
            const data1 = [];
            let remainingInterest1 = interest1;
            for (let i = 0; i < term1; i++) {
                const yearlyInterest = remainingInterest1 / (term1 - i);
                data1.push(remainingInterest1);
                remainingInterest1 -= yearlyInterest;
            }
            
            // Fill with zeros if term1 < maxTerm
            while (data1.length < maxTerm) {
                data1.push(0);
            }
            
            // Calculate interest paid per year for scenario 2
            const data2 = [];
            let remainingInterest2 = interest2;
            for (let i = 0; i < term2; i++) {
                const yearlyInterest = remainingInterest2 / (term2 - i);
                data2.push(remainingInterest2);
                remainingInterest2 -= yearlyInterest;
            }
            
            // Fill with zeros if term2 < maxTerm
            while (data2.length < maxTerm) {
                data2.push(0);
            }
            
            // Create new chart
            comparisonChart = new Chart(ctx, {
                type: 'line',
                data: {
                    labels: labels,
                    datasets: [
                        {
                            label: 'Scenario 1',
                            data: data1,
                            borderColor: '#3b82f6',
                            backgroundColor: 'rgba(59, 130, 246, 0.1)',
                            fill: true,
                            tension: 0.1
                        },
                        {
                            label: 'Scenario 2',
                            data: data2,
                            borderColor: '#10b981',
                            backgroundColor: 'rgba(16, 185, 129, 0.1)',
                            fill: true,
                            tension: 0.1
                        }
                    ]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        y: {
                            beginAtZero: true,
                            ticks: {
                                callback: function(value) {
                                    return '$' + value.toLocaleString();
                                }
                            }
                        }
                    },
                    plugins: {
                        tooltip: {
                            callbacks: {
                                label: function(context) {
                                    return context.dataset.label + ': $' + context.raw.toLocaleString();
                                }
                            }
                        }
                    }
                }
            });
        }
        
        // Generate amortization schedule
        function generateAmortizationSchedule() {
            const loanAmount = homePrice - downPayment;
            const monthlyRate = interestRate / 100 / 12;
            const numberOfPayments = loanTerm * 12;
            
            let monthlyPayment = 0;
            if (monthlyRate > 0) {
                monthlyPayment = loanAmount * monthlyRate * Math.pow(1 + monthlyRate, numberOfPayments) / (Math.pow(1 + monthlyRate, numberOfPayments) - 1);
            } else {
                monthlyPayment = loanAmount / numberOfPayments;
            }
            
            const schedule = [];
            let balance = loanAmount;
            let totalInterest = 0;
            
            for (let i = 1; i <= numberOfPayments; i++) {
                const interestPayment = balance * monthlyRate;
                const principalPayment = monthlyPayment - interestPayment;
                
                totalInterest += interestPayment;
                balance -= principalPayment;
                
                if (balance < 0) balance = 0;
                
                schedule.push({
                    payment: i,
                    date: new Date(new Date().setMonth(new Date().getMonth() + i)),
                    monthlyPayment: monthlyPayment,
                    principal: principalPayment,
                    interest: interestPayment,
                    totalInterest: totalInterest,
                    balance: balance
                });
            }
            
            return schedule;
        }
        
        // Update amortization table
        function updateAmortizationTable() {
            const schedule = generateAmortizationSchedule();
            const tableBody = document.getElementById('amortization-table');
            const viewType = document.getElementById('amortization-view').value;
            const yearsToShow = document.getElementById('amortization-years').value;
            
            // Clear existing table
            tableBody.innerHTML = '';
            
            let displaySchedule = [];
            
            if (viewType === 'yearly') {
                // Group by year
                for (let year = 1; year <= loanTerm; year++) {
                    const yearlyPayments = schedule.filter(payment => 
                        Math.ceil(payment.payment / 12) === year
                    );
                    
                    if (yearlyPayments.length > 0) {
                        const lastPaymentOfYear = yearlyPayments[yearlyPayments.length - 1];
                        
                        displaySchedule.push({
                            period: `Year ${year}`,
                            date: lastPaymentOfYear.date,
                            monthlyPayment: lastPaymentOfYear.monthlyPayment,
                            principal: yearlyPayments.reduce((sum, payment) => sum + payment.principal, 0),
                            interest: yearlyPayments.reduce((sum, payment) => sum + payment.interest, 0),
                            totalInterest: lastPaymentOfYear.totalInterest,
                            balance: lastPaymentOfYear.balance
                        });
                    }
                }
            } else {
                // Monthly view
                displaySchedule = schedule;
            }
            
            // Limit years to show if needed
            if (yearsToShow !== 'all') {
                const paymentsToShow = parseInt(yearsToShow) * (viewType === 'yearly' ? 1 : 12);
                displaySchedule = displaySchedule.slice(0, paymentsToShow);
            }
            
            // Populate table
            displaySchedule.forEach(row => {
                const tr = document.createElement('tr');
                tr.className = 'amortization-row';
                
                // Format date
                const date = row.date.toLocaleDateString('en-US', { 
                    year: 'numeric', 
                    month: 'short'
                });
                
                // Create cells
                tr.innerHTML = `
                    <td class="p-3">${viewType === 'yearly' ? row.period : `${row.payment} (${date})`}</td>
                    <td class="p-3 text-right">${formatCurrency(row.monthlyPayment)}</td>
                    <td class="p-3 text-right">${formatCurrency(row.principal)}</td>
                    <td class="p-3 text-right">${formatCurrency(row.interest)}</td>
                    <td class="p-3 text-right">${formatCurrency(row.totalInterest)}</td>
                    <td class="p-3 text-right">${formatCurrency(row.balance)}</td>
                `;
                
                tableBody.appendChild(tr);
            });
            
            // Initialize amortization chart if needed
            initAmortizationChart();
        }
        
        // Initialize the amortization chart
        function initAmortizationChart() {
            const ctx = document.getElementById('amortization-chart').getContext('2d');
            const schedule = generateAmortizationSchedule();
            
            // Destroy existing chart if it exists
            if (amortizationChart) {
                amortizationChart.destroy();
            }
            
            // Prepare data for chart - group by year
            const years = [];
            const principalData = [];
            const interestData = [];
            
            for (let year = 1; year <= loanTerm; year++) {
                years.push(`Year ${year}`);
                
                const yearlyPayments = schedule.filter(payment => 
                    Math.ceil(payment.payment / 12) === year
                );
                
                const yearlyPrincipal = yearlyPayments.reduce((sum, payment) => sum + payment.principal, 0);
                const yearlyInterest = yearlyPayments.reduce((sum, payment) => sum + payment.interest, 0);
                
                principalData.push(yearlyPrincipal);
                interestData.push(yearlyInterest);
            }
            
            // Create new chart
            amortizationChart = new Chart(ctx, {
                type: 'bar',
                data: {
                    labels: years,
                    datasets: [
                        {
                            label: 'Principal',
                            data: principalData,
                            backgroundColor: '#3b82f6'
                        },
                        {
                            label: 'Interest',
                            data: interestData,
                            backgroundColor: '#ef4444'
                        }
                    ]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        x: {
                            stacked: true
                        },
                        y: {
                            stacked: true,
                            ticks: {
                                callback: function(value) {
                                    return '$' + value.toLocaleString();
                                }
                            }
                        }
                    },
                    plugins: {
                        tooltip: {
                            callbacks: {
                                label: function(context) {
                                    return context.dataset.label + ': $' + context.raw.toLocaleString();
                                }
                            }
                        }
                    }
                }
            });
        }
        
        // Export amortization schedule
        function exportAmortizationSchedule() {
            const schedule = generateAmortizationSchedule();
            const viewType = document.getElementById('amortization-view').value;
            
            let csvContent = "data:text/csv;charset=utf-8,";
            csvContent += "Period,Date,Payment,Principal,Interest,Total Interest,Balance\n";
            
            if (viewType === 'yearly') {
                // Group by year
                for (let year = 1; year <= loanTerm; year++) {
                    const yearlyPayments = schedule.filter(payment => 
                        Math.ceil(payment.payment / 12) === year
                    );
                    
                    if (yearlyPayments.length > 0) {
                        const lastPaymentOfYear = yearlyPayments[yearlyPayments.length - 1];
                        const date = lastPaymentOfYear.date.toLocaleDateString('en-US');
                        const principal = yearlyPayments.reduce((sum, payment) => sum + payment.principal, 0);
                        const interest = yearlyPayments.reduce((sum, payment) => sum + payment.interest, 0);
                        
                        csvContent += `Year ${year},${date},${lastPaymentOfYear.monthlyPayment.toFixed(2)},${principal.toFixed(2)},${interest.toFixed(2)},${lastPaymentOfYear.totalInterest.toFixed(2)},${lastPaymentOfYear.balance.toFixed(2)}\n`;
                    }
                }
            } else {
                // Monthly view
                schedule.forEach(row => {
                    const date = row.date.toLocaleDateString('en-US');
                    csvContent += `${row.payment},${date},${row.monthlyPayment.toFixed(2)},${row.principal.toFixed(2)},${row.interest.toFixed(2)},${row.totalInterest.toFixed(2)},${row.balance.toFixed(2)}\n`;
                });
            }
            
            // Create download link
            const encodedUri = encodeURI(csvContent);
            const link = document.createElement("a");
            link.setAttribute("href", encodedUri);
            link.setAttribute("download", "mortgage_amortization_schedule.csv");
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
        }
        
        // Calculate impact of extra payments
        function calculateExtraPayments() {
            const extraMonthly = parseFloat(document.getElementById('extra-monthly').value) || 0;
            const extraAnnual = parseFloat(document.getElementById('extra-annual').value) || 0;
            const extraOnetimeAmount = parseFloat(document.getElementById('extra-onetime-amount').value) || 0;
            const extraOnetimeMonth = parseInt(document.getElementById('extra-onetime-month').value) || 0;
            
            // Generate regular schedule
            const regularSchedule = generateAmortizationSchedule();
            
            // Generate schedule with extra payments
            const loanAmount = homePrice - downPayment;
            const monthlyRate = interestRate / 100 / 12;
            const numberOfPayments = loanTerm * 12;
            
            let monthlyPayment = 0;
            if (monthlyRate > 0) {
                monthlyPayment = loanAmount * monthlyRate * Math.pow(1 + monthlyRate, numberOfPayments) / (Math.pow(1 + monthlyRate, numberOfPayments) - 1);
            } else {
                monthlyPayment = loanAmount / numberOfPayments;
            }
            
            const extraSchedule = [];
            let balance = loanAmount;
            let totalInterest = 0;
            let paymentCount = 0;
            
            while (balance > 0 && paymentCount < numberOfPayments) {
                paymentCount++;
                
                // Calculate extra payment for this month
                let extraPayment = extraMonthly;
                
                // Add annual extra payment if it's December
                if (paymentCount % 12 === 0) {
                    extraPayment += extraAnnual;
                }
                
                // Add one-time payment if this is the specified month
                if (paymentCount === extraOnetimeMonth) {
                    extraPayment += extraOnetimeAmount;
                }
                
                const interestPayment = balance * monthlyRate;
                const principalPayment = monthlyPayment - interestPayment + extraPayment;
                
                totalInterest += interestPayment;
                balance -= principalPayment;
                
                if (balance < 0) balance = 0;
                
                extraSchedule.push({
                    payment: paymentCount,
                    date: new Date(new Date().setMonth(new Date().getMonth() + paymentCount)),
                    monthlyPayment: monthlyPayment + extraPayment,
                    principal: principalPayment,
                    interest: interestPayment,
                    totalInterest: totalInterest,
                    balance: balance,
                    extraPayment: extraPayment
                });
            }
            
            // Calculate savings
            const originalTerm = loanTerm;
            const newTerm = Math.ceil(paymentCount / 12);
            const newMonths = paymentCount % 12;
            
            const timeSavedYears = originalTerm - newTerm;
            const timeSavedMonths = newMonths === 0 ? 0 : 12 - newMonths;
            
            const originalInterest = regularSchedule[regularSchedule.length - 1].totalInterest;
            const newInterest = totalInterest;
            const interestSavings = originalInterest - newInterest;
            
            const totalExtraPayments = extraSchedule.reduce((sum, payment) => sum + payment.extraPayment, 0);
            
            // Update UI
            document.getElementById('original-term').textContent = `${originalTerm} years`;
            
            if (newMonths === 0) {
                document.getElementById('new-term').textContent = `${newTerm} years`;
            } else {
                document.getElementById('new-term').textContent = `${newTerm} years ${newMonths} months`;
            }
            
            if (timeSavedYears === 0 && timeSavedMonths === 0) {
                document.getElementById('time-saved').textContent = 'None';
            } else if (timeSavedYears === 0) {
                document.getElementById('time-saved').textContent = `${timeSavedMonths} months`;
            } else if (timeSavedMonths === 0) {
                document.getElementById('time-saved').textContent = `${timeSavedYears} years`;
            } else {
                document.getElementById('time-saved').textContent = `${timeSavedYears} years ${timeSavedMonths} months`;
            }
            
            document.getElementById('interest-saved').textContent = formatCurrency(interestSavings);
            document.getElementById('total-extra').textContent = formatCurrency(totalExtraPayments);
            
            // Update charts
            initExtraPaymentCharts(regularSchedule, extraSchedule);
        }
        
        // Initialize extra payment charts
        function initExtraPaymentCharts(regularSchedule, extraSchedule) {
            // Payment comparison chart
            const paymentCtx = document.getElementById('extra-payment-chart').getContext('2d');
            
            // Destroy existing chart if it exists
            if (extraPaymentChart) {
                extraPaymentChart.destroy();
            }
            
            // Group data by year for regular schedule
            const regularYears = [];
            const regularPayments = [];
            
            for (let year = 1; year <= loanTerm; year++) {
                regularYears.push(`Year ${year}`);
                
                const yearlyPayments = regularSchedule.filter(payment => 
                    Math.ceil(payment.payment / 12) === year
                );
                
                const yearlyTotal = yearlyPayments.reduce((sum, payment) => sum + payment.monthlyPayment, 0);
                regularPayments.push(yearlyTotal);
            }
            
            // Group data by year for extra payment schedule
            const extraYears = [];
            const extraPayments = [];
            const extraAmounts = [];
            
            const maxExtraYears = Math.ceil(extraSchedule.length / 12);
            
            for (let year = 1; year <= maxExtraYears; year++) {
                extraYears.push(`Year ${year}`);
                
                const yearlyPayments = extraSchedule.filter(payment => 
                    Math.ceil(payment.payment / 12) === year
                );
                
                const yearlyTotal = yearlyPayments.reduce((sum, payment) => sum + payment.monthlyPayment, 0);
                const yearlyExtra = yearlyPayments.reduce((sum, payment) => sum + payment.extraPayment, 0);
                
                extraPayments.push(yearlyTotal);
                extraAmounts.push(yearlyExtra);
            }
            
            // Create new payment chart
            extraPaymentChart = new Chart(paymentCtx, {
                type: 'bar',
                data: {
                    labels: regularYears,
                    datasets: [
                        {
                            label: 'Regular Payments',
                            data: regularPayments,
                            backgroundColor: '#3b82f6'
                        },
                        {
                            label: 'With Extra Payments',
                            data: extraPayments,
                            backgroundColor: '#10b981'
                        }
                    ]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        y: {
                            beginAtZero: true,
                            ticks: {
                                callback: function(value) {
                                    return '$' + value.toLocaleString();
                                }
                            }
                        }
                    },
                    plugins: {
                        tooltip: {
                            callbacks: {
                                label: function(context) {
                                    return context.dataset.label + ': $' + context.raw.toLocaleString();
                                }
                            }
                        }
                    }
                }
            });
            
            // Balance reduction chart
            const balanceCtx = document.getElementById('balance-reduction-chart').getContext('2d');
            
            // Destroy existing chart if it exists
            if (balanceReductionChart) {
                balanceReductionChart.destroy();
            }
            
            // Prepare data for balance chart
            const regularBalances = [];
            const extraBalances = [];
            
            // Get balance at the end of each year
            for (let year = 1; year <= loanTerm; year++) {
                const regularYearEnd = regularSchedule.find(payment => payment.payment === year * 12);
                
                if (regularYearEnd) {
                    regularBalances.push(regularYearEnd.balance);
                } else {
                    regularBalances.push(0);
                }
                
                const extraYearEnd = extraSchedule.find(payment => payment.payment === year * 12);
                
                if (extraYearEnd) {
                    extraBalances.push(extraYearEnd.balance);
                } else {
                    extraBalances.push(0);
                }
            }
            
            // Create new balance chart
            balanceReductionChart = new Chart(balanceCtx, {
                type: 'line',
                data: {
                    labels: regularYears,
                    datasets: [
                        {
                            label: 'Regular Balance',
                            data: regularBalances,
                            borderColor: '#3b82f6',
                            backgroundColor: 'rgba(59, 130, 246, 0.1)',
                            fill: true
                        },
                        {
                            label: 'With Extra Payments',
                            data: extraBalances,
                            borderColor: '#10b981',
                            backgroundColor: 'rgba(16, 185, 129, 0.1)',
                            fill: true
                        }
                    ]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        y: {
                            beginAtZero: true,
                            ticks: {
                                callback: function(value) {
                                    return '$' + value.toLocaleString();
                                }
                            }
                        }
                    },
                    plugins: {
                        tooltip: {
                            callbacks: {
                                label: function(context) {
                                    return context.dataset.label + ': $' + context.raw.toLocaleString();
                                }
                            }
                        }
                    }
                }
            });
        }
        
        // Format currency values
        function formatCurrency(value, showSign = false) {
            const formatter = new Intl.NumberFormat('en-US', {
                style: 'currency',
                currency: 'USD',
                minimumFractionDigits: 2,
                maximumFractionDigits: 2
            });
            
            if (showSign && value > 0) {
                return '+' + formatter.format(value);
            } else {
                return formatter.format(value);
            }
        }
        
        // Initialize the calculator when the page loads
        window.addEventListener('DOMContentLoaded', () => {
            initCalculator();
            initPaymentChart();
        });
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'94afe019330bb47c',t:'MTc0OTEyODY2Mi4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
