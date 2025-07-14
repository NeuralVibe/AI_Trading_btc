# Security Policy

## Supported Versions

| Version | Supported          |
| ------- | ------------------ |
| 1.0.x   | :white_check_mark: |

## Reporting a Vulnerability

If you discover a security vulnerability, please report it by emailing us directly. Please do not create a public GitHub issue for security vulnerabilities.

### What to Include

- Description of the vulnerability
- Steps to reproduce the issue
- Potential impact
- Suggested fix (if any)

### Response Timeline

- We will acknowledge receipt of your vulnerability report within 48 hours
- We will provide a detailed response within 7 days
- We will work on a fix and provide updates on our progress

## Security Best Practices

### API Key Management
- Never commit `.env` files to version control
- Use strong, unique API keys
- Enable IP restrictions on Upbit API
- Regularly rotate API keys

### Server Security
- Use firewall rules to restrict access
- Keep system packages updated
- Monitor logs for suspicious activity
- Use HTTPS for all external communications

### Trading Security
- Start with small amounts for testing
- Monitor trading activity regularly
- Set up proper alerting systems
- Understand the risks involved

## Known Security Considerations

1. **API Rate Limits**: The bot respects exchange API rate limits
2. **Error Handling**: Comprehensive error handling prevents unexpected behavior
3. **Logging**: Sensitive information is not logged
4. **Dependencies**: Regular security updates for all dependencies

## Contact

For security-related questions or concerns, please contact the maintainers directly.
