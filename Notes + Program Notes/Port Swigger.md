
# Lab: OS command injection, simple case

Click on a product on the website
Go to the part of the page that checks stocks
Use Burp to Proxy the website and look for the "productid=1&storeId=1"
Replace the "1" after StoreID and replace it with "1 | whoami"
This gives you the name "peter-CWPc9J"
	This chain allows you to see who is running the system by using the command 
	"1 | whoami"
	| = f(g(x))
	whoami = Tells who you or someone else is

Lab: DOM XSS in `innerHTML` sink using source `location.search`
1. Enter the following into the into the search box:
    
    `<img src=1 onerror=alert(1)>`
2. Click "Search".

Lab: DOM XSS in jQuery anchor `href` attribute sink using `location.search` source
1. On the Submit feedback page, change the query parameter `returnPath` to `/` followed by a random alphanumeric string.
2. Right-click and inspect the element, and observe that your random string has been placed inside an a `href` attribute.
3. Change `returnPath` to:
    
    `javascript:alert(document.cookie)`
    
    Hit enter and click "back".

Lab: DOM XSS in jQuery selector sink using a hash change event
1. Notice the vulnerable code on the home page using Burp or the browser's Dev Tools.
2. From the lab banner, open the exploit server.
3. In the **Body** section, add the following malicious `iframe`:
    
    `<iframe src="https://YOUR-LAB-ID.web-security-academy.net/#" onload="this.src+='<img src=x onerror=print()>'"></iframe>`
4. Store the exploit, then click **View exploit** to confirm that the `print()` function is called.
5. Go back to the exploit server and click **Deliver to victim** to solve the lab.