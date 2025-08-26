# 🕵️ URL Hops Inspector

Inspect and analyze the full chain of **HTTP URL hops** caused by redirections, complete with metadata!  
This Python-based tool follows URL redirect chains, allowing you to inspect **response status codes**, **headers**, and **response body previews** at every step.  
With support for **proxy configurations**, it's your go-to utility for web debugging, redirect analysis, or understanding how URL shorteners work.

## 🚀 Features

- **Trace URL Hops**: Follow each step in the HTTP redirection chain to the final destination.
- **Inspect HTTP Metadata**: View HTTP status codes, headers, and preview parts of the response body for debugging.
- **End-to-End Analysis**: See the full URL journey from the initial input to the final resolved URL.
- **Proxy Support**: Configure HTTP/HTTPS proxies to route requests through custom servers.
- **Lightweight and Easy to Use**: Built with Python and the popular `requests` library.

## 📦 Installation

1. Clone the repository:
  ```bash
  git clone https://github.com/<your-username>/url-hops-inspector.git
  cd url-hops-inspector
  ```

Note: The tool primarily uses the requests library. Ensure Python 3.6 or higher is installed.

## 🛠️ Usage
1. Run Interactively
   
  You can run the script interactively in your terminal or within a Jupyter Notebook.
  
  Example in Terminal:

  ```bash
  python url_hops_inspector.py
  ```

  Input in the terminal:
  ```bash
  Please enter the URL to trace: https://bit.ly/3xyzAbc
  Enter proxy URL (or leave blank to skip): http://123.45.67.89:8888
  ```

  Example Output:
  ```bash
  Tracing URL redirects for: https://bit.ly/3xyzAbc
  --------------------------------------------------
  Hop #1
  Request URL: https://bit.ly/3xyzAbc
  Status Code: 301
  Headers:
    Location: https://example.com/somewhere
  Response body (limit 200 chars):
    <html>Redirecting...</html>
  --------------------------------------------------
  Hop #2
  Request URL: https://example.com/somewhere
  Status Code: 302
  Headers:
    Location: https://example.com/destination
  Response body (limit 200 chars):
    <html>Temporary Redirect...</html>
  --------------------------------------------------
  
  Final Destination:
  URL: https://example.com/destination
  Status Code: 200
  Headers:
    Content-Type: text/html
  Response body (limit 200 chars):
    <html><body>Welcome!</body></html>
  ```
2. As a Jupyter Notebook

You can open the provided Jupyter Notebook version (url_hops_inspector.ipynb) to use the tool interactively.

3. Using Proxies

To hide your IP address or test from a different location, you can configure a proxy. Here’s an example of how to use one:
    
    HTTP proxy: http://123.45.67.89:8080
    HTTPS proxy: https://proxyserver.com:443

Simply enter the proxy URL when prompted, or leave it blank for no proxy.

## 📝 Example Python Code

If you want to integrate this tool into your own projects, here’s a simple example of how to use the trace_url_jumps_with_details function:
from url_hops_inspector import trace_url_jumps_with_details

  ```python
  url_to_trace = "https://bit.ly/3xyzAbc"
  proxy_url = "http://123.45.67.89:8080"  # Proxy (optional)
  
  final_url = trace_url_jumps_with_details(url_to_trace, proxy=proxy_url)
  print("Final URL:", final_url)
  ```

## ⚠️ Limitations to Keep in Mind

1. Handling Redirect Loops: The tool automatically limits redirects to 30 hops by default to prevent infinite loops.
2. Truncated Response Bodies: Only the first 200 characters of the response body are shown by default. This limit is configurable.
3. Proxies: Free or public proxies can be unreliable or slow. Use trusted proxies for the best experience.
4. Respect Terms of Service: When tracing URLs, ensure you comply with the terms of service of the target websites.

## 🌐 Use Cases

- Debugging redirect chains for shortened URLs (e.g., bit.ly, t.co).
- Checking and validating final destinations for campaign/marketing URLs.
- Analyzing website behavior for redirections or affiliate links.
- Privacy-friendly request tracing using custom proxies.

## 🤝 Contributing

Interested in improving URL Hops Inspector? Contributions are welcome! Here’s how to get started:

1. Fork the repository.
2. Create a feature branch:
  ```bash
  git checkout -b my-feature
  ```
3. Commit your changes:
  ```bash
  git commit -m "Add my awesome feature"
4. Push to your branch:
  ```bash
  git push origin my-feature
  ```
3. Submit a pull request for review 🚀.

## 📜 License

This project is licensed under the MIT License, making it free for personal and commercial use.

## 🙌 Acknowledgments

Built with ❤️ using Python and Requests.
Inspired by a need for transparent and detailed HTTP debugging tools.
Thanks to the open-source community for their continuous support!
