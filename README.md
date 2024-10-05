<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <title>লটারি সিস্টেম</title>
    <!-- Bootstrap CSS CDN -->
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/css/bootstrap.min.css">
    <!-- Font Awesome for Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.2/css/all.min.css">
    <style>
        /* Gradient Background */
        body {
            background: linear-gradient(135deg, #f8f9fa, #e9ecef);
            min-height: 100vh;
        }
        .container {
            margin-top: 30px;
        }
        .footer {
            margin-top: 50px;
            padding: 20px 0;
            background-color: #343a40;
            color: white;
            text-align: center;
        }
        .lottery-number {
            cursor: pointer;
            transition: transform 0.2s;
            position: relative;
            padding: 20px;
            border: 3px solid #28a745; /* Green border */
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
            font-size: 1.2em;
            text-align: center;
            color: #28a745; /* Green text */
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 10px; /* Add margin to align evenly */
            height: 120px; /* Set height to maintain the size */
            background-color: rgba(40, 167, 69, 0.1); /* Light green background */
            animation: neon-border 1.5s infinite alternate;
        }
        @keyframes neon-border {
            0% { border-color: #28a745; box-shadow: 0 0 10px #28a745; }
            100% { border-color: #33ff00; box-shadow: 0 0 20px #33ff00; }
        }
        .serial-number {
            position: absolute;
            top: 10px; /* Align to top */
            left: 10px; /* Align to left */
            font-size: 0.8em;
            color: #fff; /* White color for serial number */
            background-color: rgba(0, 0, 0, 0.5); /* Semi-transparent background */
            padding: 5px;
            border-radius: 5px;
        }
        .ticket-status {
            font-size: 1.5em;
            color: #28a745;
        }
        .bought {
            color: red;
        }
        /* Button Styles */
        .btn-deposit, .btn-withdraw {
            width: 100%;
            margin: 5px 0;
        }
        /* Ticket Icon Style */
        .ticket-icon {
            color: #4267B2; /* Facebook Verified Blue color */
            font-size: 3em; /* Increase the icon size */
        }
        /* Sidebar styles */
        .sidebar {
            position: fixed;
            top: 0;
            left: -250px; /* Hidden by default */
            height: 100vh;
            background-color: #f8f9fa; /* Opaque background color */
            padding: 15px;
            width: 250px;
            box-shadow: 2px 0 5px rgba(0, 0, 0, 0.1);
            transition: left 0.3s ease; /* Smooth transition for slide-in/out */
        }
        .sidebar.show {
            left: 0; /* Show sidebar */
        }
        .sidebar h2 {
            font-size: 1.5em;
            margin-bottom: 20px;
        }
        .sidebar a {
            display: block;
            padding: 10px;
            color: #28a745;
            text-decoration: none;
            border-radius: 5px;
            margin-bottom: 10px;
            transition: background 0.3s;
        }
        .sidebar a:hover {
            background-color: #e9ecef;
        }
        .main-content {
            padding: 20px;
        }
        /* Toggle Button Style */
        .toggle-btn {
            position: fixed;
            top: 20px;
            left: 20px;
            z-index: 1000;
        }
    </style>
</head>
<body>

    <!-- Toggle Button -->
    <button class="btn btn-primary toggle-btn" onclick="toggleSidebar()">
        <i class="fas fa-bars"></i>
    </button>

    <!-- Sidebar Navigation -->
    <div class="sidebar" id="sidebar">
        <h2>নেভিগেশন</h2>
        <a href="#" data-toggle="modal" data-target="#depositModal">ডিপোজিট</a>
        <a href="#" data-toggle="modal" data-target="#withdrawModal">উল্টো</a>
        <a href="#">হোম</a>
        <a href="#">আমাদের সম্পর্কে</a>
        <a href="#">যোগাযোগ</a>
    </div>

    <div class="main-content">
        <h1 class="text-center">লটারি সিস্টেম</h1>
        <p class="text-center">আপনার টিকিট কিনুন এবং জিতুন!</p>
        
        <div class="row">
            <div class="col-md-4">
                <div class="lottery-number" onclick="buyTicket(1)">
                    <span class="ticket-icon">🎟</span>
                    <span class="serial-number" id="ticket1-serial">12345678910</span>
                    <span class="ticket-status" id="ticket1-status">৳10</span>
                </div>
            </div>
            <div class="col-md-4">
                <div class="lottery-number" onclick="buyTicket(2)">
                    <span class="ticket-icon">🎟</span>
                    <span class="serial-number" id="ticket2-serial">12345678910</span>
                    <span class="ticket-status" id="ticket2-status">৳10</span>
                </div>
            </div>
            <div class="col-md-4">
                <div class="lottery-number" onclick="buyTicket(3)">
                    <span class="ticket-icon">🎟</span>
                    <span class="serial-number" id="ticket3-serial">12345678910</span>
                    <span class="ticket-status" id="ticket3-status">৳10</span>
                </div>
            </div>
            <div class="col-md-4">
                <div class="lottery-number" onclick="buyTicket(4)">
                    <span class="ticket-icon">🎟</span>
                    <span class="serial-number" id="ticket4-serial">12345678910</span>
                    <span class="ticket-status" id="ticket4-status">৳10</span>
                </div>
            </div>
            <div class="col-md-4">
                <div class="lottery-number" onclick="buyTicket(5)">
                    <span class="ticket-icon">🎟</span>
                    <span class="serial-number" id="ticket5-serial">12345678910</span>
                    <span class="ticket-status" id="ticket5-status">৳10</span>
                </div>
            </div>
            <div class="col-md-4">
                <div class="lottery-number" onclick="buyTicket(6)">
                    <span class="ticket-icon">🎟</span>
                    <span class="serial-number" id="ticket6-serial">12345678910</span>
                    <span class="ticket-status" id="ticket6-status">৳10</span>
                </div>
            </div>
            <div class="col-md-4">
                <div class="lottery-number" onclick="buyTicket(7)">
                    <span class="ticket-icon">🎟</span>
                    <span class="serial-number" id="ticket7-serial">12345678910</span>
                    <span class="ticket-status" id="ticket7-status">৳10</span>
                </div>
            </div>
            <div class="col-md-4">
                <div class="lottery-number" onclick="buyTicket(8)">
                    <span class="ticket-icon">🎟</span>
                    <span class="serial-number" id="ticket8-serial">12345678910</span>
                    <span class="ticket-status" id="ticket8-status">৳10</span>
                </div>
            </div>
            <div class="col-md-4">
                <div class="lottery-number" onclick="buyTicket(9)">
                    <span class="ticket-icon">🎟</span>
                    <span class="serial-number" id="ticket9-serial">12345678910</span>
                    <span class="ticket-status" id="ticket9-status">৳10</span>
                </div>
            </div>
            <div class="col-md-4">
                <div class="lottery-number" onclick="buyTicket(10)">
                    <span class="ticket-icon">🎟</span>
                    <span class="serial-number" id="ticket10-serial">12345678910</span>
                    <span class="ticket-status" id="ticket10-status">৳10</span>
                </div>
            </div>
        </div>

        <!-- Deposit Modal -->
        <div class="modal fade" id="depositModal" tabindex="-1" role="dialog" aria-labelledby="depositModalLabel" aria-hidden="true">
            <div class="modal-dialog" role="document">
                <div class="modal-content">
                    <div class="modal-header">
                        <h5 class="modal-title" id="depositModalLabel">ডিপোজিট অপশন</h5>
                        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                            <span aria-hidden="true">&times;</span>
                        </button>
                    </div>
                    <div class="modal-body">
                        <p>আপনার পেমেন্ট সম্পন্ন করতে নিম্নলিখিত অপশনগুলোতে ক্লিক করুন।</p>
                        <button class="btn btn-deposit" onclick="redirectToPayment('bikash')">বিকাশ</button>
                        <button class="btn btn-deposit" onclick="redirectToPayment('nagad')">নগদ</button>
                        <button class="btn btn-deposit" onclick="redirectToPayment('rocket')">রকেট</button>
                    </div>
                </div>
            </div>
        </div>

        <!-- Withdraw Modal -->
        <div class="modal fade" id="withdrawModal" tabindex="-1" role="dialog" aria-labelledby="withdrawModalLabel" aria-hidden="true">
            <div class="modal-dialog" role="document">
                <div class="modal-content">
                    <div class="modal-header">
                        <h5 class="modal-title" id="withdrawModalLabel">উল্টো অপশন</h5>
                        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                            <span aria-hidden="true">&times;</span>
                        </button>
                    </div>
                    <div class="modal-body">
                        <p>আপনার পেমেন্ট উল্টো করার জন্য নিম্নলিখিত অপশনগুলোতে ক্লিক করুন।</p>
                        <button class="btn btn-withdraw" onclick="redirectToWithdrawal('bikash')">বিকাশ</button>
                        <button class="btn btn-withdraw" onclick="redirectToWithdrawal('nagad')">নগদ</button>
                        <button class="btn btn-withdraw" onclick="redirectToWithdrawal('rocket')">রকেট</button>
                    </div>
                </div>
            </div>
        </div>

        <div class="footer">
            <p>যোগাযোগ: <a href="https://t.me/12345678910" target="_blank" style="color: white;">টেলিগ্রাম</a></p>
            <p>© 2024 লটারি সিস্টেম</p>
        </div>
    </div>

    <!-- jQuery and Bootstrap JS -->
    <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.9.2/dist/umd/popper.min.js"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/js/bootstrap.min.js"></script>

    <script>
        function buyTicket(ticketId) {
            const ticketStatus = document.getElementById(`ticket${ticketId}-status`);
            const serialNumber = Math.floor(Math.random() * 10000000000); // Generate random serial number
            document.getElementById(`ticket${ticketId}-serial`).innerText = serialNumber; // Display serial number

            ticketStatus.innerHTML = "<span class='bought'>টিকেট ক্রয় সম্পন্ন!</span>";
            // Redirect to buy option
            setTimeout(() => {
                alert("টিকেটটি ক্রয় করতে নিচের পেমেন্ট অপশন নির্বাচন করুন।");
                $('#depositModal').modal('show');
            }, 500);
        }

        function redirectToPayment(option) {
            // Redirect logic for deposit payment
            window.location.href = `payment.html?method=deposit&option=${option}`;
        }

        function redirectToWithdrawal(option) {
            // Redirect logic for withdrawal payment
            window.location.href = `payment.html?method=withdrawal&option=${option}`;
        }

        function toggleSidebar() {
            const sidebar = document.getElementById("sidebar");
            sidebar.classList.toggle("show");
        }
    </script>
</body>
</html>
