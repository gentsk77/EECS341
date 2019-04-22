$$\prod_{p.name, f.departure\_datetime, departure.name, arrival.name}$$

$$ ~ $$

$$  \sigma_{p.id = t.passenger\_id ~ \wedge ~ p.id = :PASS\_ID ~ \wedge ~ t.flight\_id = f.id ~ \wedge ~ f.route\_id = r.id ~ \wedge ~ f.departure\_datetime > now() ~ \wedge ~ arrival.name = r.arrival\_airport ~ \wedge ~ departure.name = r.departure\_airport} $$

$$ ~$$

$$ \times $$

$$  ~ $$

$$ \rho_p(passenger) \space \space \space \space \space  \times $$

$$  ~ $$

$$ \space \space \space \space \space  \space \space \space \space \space  \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \rho_t(ticket) \space \space \space \space \space  \times $$

$$  ~ $$

$$ \space \space \space \space \space  \space \space \space \space \space  \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \rho_f(flight) \space \space \space \space \space  \times $$

$$  ~ $$

$$ \space \space \space \space \space  \space \space \space \space \space  \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \rho_r(route) \space \space \space \space \space  \times $$

$$  ~ $$

$$ \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space  \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \rho_{departure}(airport) \space \space \space \space \space   \space \space \space \space \space    \rho_{arrival}(airport)$$