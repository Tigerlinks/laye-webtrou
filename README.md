# laye-webtrou
simple steps to troubleshoot common website issues like; connectivity problems, timeout, and unexpected HTTP status codes
import requests
import time

def check_website(url):
    try:
        start_time = time.time()
        response = requests.get(url, timeout=10)
        end_time = time.time()

        print(f"URL: {url}")
        print(f"Status Code: {response.status_code}")
        print(f"Response Time: {end_time - start_time:.2f} seconds")

        if response.status_code == 200:
            print("Website is reachable.")
        else:
            print("Website returned an unexpected status code.")

    except requests.exceptions.Timeout:
        print("Error: Request timed out.")
    except requests.exceptions.ConnectionError:
        print("Error: Unable to connect to the website.")
    except requests.exceptions.RequestException as e:
        print(f"Error: {e}")

if __name__ == "__main__":
    website_url = input("Enter website URL: ")
    check_website(website_url)
