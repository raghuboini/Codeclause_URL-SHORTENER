
import string
import random

class URLShortener:
    def __init__(self):
        self.url_mapping = {}
        self.characters = string.ascii_letters + string.digits
        self.base_url = "https://short.url/"

    def generate_short_url(self, original_url, length=6):
        while True:
            short_url = "".join(random.choice(self.characters) for _ in range(length))
            if short_url not in self.url_mapping:
                self.url_mapping[short_url] = original_url
                return self.base_url + short_url

    def get_original_url(self, short_url):
        short_url = short_url.replace(self.base_url, "")
        return self.url_mapping.get(short_url, None)

# Example usage:
if __name__ == "__main__":
    shortener = URLShortener()
    original_url = "https://www.example.com"
    short_url = shortener.generate_short_url(original_url)
    print("Shortened URL:", short_url)

    retrieved_url = shortener.get_original_url(short_url)
    print("Retrieved URL:", retrieved_url)
