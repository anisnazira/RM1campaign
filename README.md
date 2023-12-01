# RM1campaign

1.	HTML FORM VALIDATION – If the user did not input required information, it will popup “…is required” at the box and prompt user to enter the value.

/*=============== VALIDATE FORM ===============*/

function validateForm() {
    var fullName = document.getElementById('fullName').value;
    var staffNo = document.getElementById('staffNo').value;
    var kulliyyahInput = document.getElementById('kulliyyahInput').value;
    var contactNo = document.getElementById('contactNo').value;
    var email = document.getElementById('email').value;
    var amount = document.getElementById('amount').value;
    var signatureInput = document.getElementById('signatureInput').value;
    var dateInput = document.getElementById('dateInput').value;

    var errorMessages = [];

    if (fullName === "") {
        errorMessages.push("Full Name is required");
    }

    if (staffNo === "") {
        errorMessages.push("Staff No. is required");
    }

    if (kulliyyahInput === "") {
        errorMessages.push("K/C/D/I/O is required");
    }

    if (contactNo === "") {
        errorMessages.push("Contact No. is required");
    }

    if (email === "") {
        errorMessages.push("Email is required");
    }

    if (amount === "") {
        errorMessages.push("Amount is required");
    }

    if (signatureInput === "") {
        errorMessages.push("Signature is required");
    }

    if (dateInput === "") {
        errorMessages.push("Date is required");
    }

    if (errorMessages.length === 0) {
        alert("Form submitted successfully!");
        document.getElementById('rm1Form').reset();
    } else {
        alert("Please fix the following errors:\n" + errorMessages.join("\n"));
    }
    return false;
}


2.	SYNC DATE AND KULLIYYAH TYPE – When user pick date and enter kulliyyah, it will update the statement below “The above salary deduction will take effect from until or further notice. For Your Kulliyyah Type”

/*===== date ===== (sync date dengan ayat bawah tu) ==*/

  document.addEventListener("DOMContentLoaded", function () {
    var startDateElement = document.getElementById('start-date');
    var endDateElement = document.getElementById('end-date');
    var dateInputElement = document.getElementById('date-input');

    var kulliyyahTypeElement = document.getElementById('kulliyyah-type');
    var kulliyyahInput = document.getElementById('kulliyyah-input');
 

    function updateKulliyyahType() {
        var enteredKulliyyah = kulliyyahInput.value.trim();
        kulliyyahTypeElement.textContent = enteredKulliyyah !== '' ? 'Kulliyyah of ' + enteredKulliyyah : 'Your Kulliyyah Type';
    }

    kulliyyahInput.addEventListener('input', function () {
        updateKulliyyahType();
    });

    // Initial update
    updateKulliyyahType();


    dateInputElement.addEventListener('input', function () {
      var selectedDate = new Date(dateInputElement.value);
      var formattedStartDate = formatDate(selectedDate);
      var formattedEndDate = calculateEndDate(selectedDate);

      startDateElement.textContent = formattedStartDate;
      endDateElement.textContent = formattedEndDate;
    });

    function formatDate(date) {
      return date.toLocaleDateString('en-US', { month: 'long', year: 'numeric' });
    }

    function calculateEndDate(startDate) {
      var endDate = new Date(startDate);
      endDate.setMonth(endDate.getMonth() + 12); 
      return formatDate(endDate);
    }
  });




3.	SCROLL UP – When the user scroll until the footer, there are scroll-up function at the bottom-right side you can click so it will bring you to the top back


/*=============== SHOW SCROLL UP ===============*/
function scrollUp() {
    const scrollUp = document.getElementById('scroll-up');
  
    if (window.scrollY >= 400) {
      scrollUp.classList.add('show-scroll');
    } else {
      scrollUp.classList.remove('show-scroll');
    }
  }
  
  window.addEventListener('scroll', scrollUp);
  



REFERENCES

1.	https://muhammadsamiullah63.blogspot.com/2023/11/html-css-js-responsive-plants-website.html (overall look and feel)

2.	https://www.youtube.com/watch?v=okbByPWS1Xc&pp=ygUNZm9ybSBodG1sIGNzcw%3D%3D (form)

